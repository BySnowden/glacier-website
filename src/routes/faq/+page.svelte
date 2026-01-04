<script lang="ts">
    import { fly } from "svelte/transition";
    import { cubicOut } from "svelte/easing";

    let y = 0;

    // Logic to fade the background layer based on scroll, just like the home page
    $: brightOpacity = Math.max(0, 1 - y / 500);

    function viewport(element: HTMLElement) {
        const observer = new IntersectionObserver(
            (entries) => {
                entries.forEach((entry) => {
                    if (entry.isIntersecting) {
                        element.classList.add("visible");
                        observer.unobserve(element);
                    }
                });
            },
            {
                threshold: 0.1,
                rootMargin: "0px 0px -50px 0px",
            },
        );
        observer.observe(element);
        return {
            destroy() {
                observer.disconnect();
            },
        };
    }
</script>

<svelte:window bind:scrollY={y} />

<svelte:head>
    <title>FAQ - Glacier Mod Manager</title>
    <link
        rel="stylesheet"
        href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css"
    />
    <link
        href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600&family=Outfit:wght@700;900&display=swap"
        rel="stylesheet"
    />
</svelte:head>

<div class="background-container">
    <div class="bg-layer dark-layer"></div>
    <div class="bg-layer bright-layer" style="opacity: {brightOpacity}"></div>
    <div class="grid-pattern"></div>
</div>

<header in:fly={{ y: -20, duration: 1000, easing: cubicOut }}>
    <div class="logo-container">
        <div class="logo-box">
            <img
                src="/images/icon-transparent.png"
                alt="Glacier Logo"
                class="logo-icon"
            />
        </div>
        <a href="/" class="logo-text-link">
            <span class="logo-text">GLACIER</span>
        </a>
    </div>

    <div class="nav-buttons">
        <a
            href="https://github.com"
            target="_blank"
            class="icon-link"
            aria-label="Visit GitHub"
        >
            <i class="fa-brands fa-github"></i>
        </a>
        <a
            href="https://ko-fi.com"
            target="_blank"
            class="icon-link"
            aria-label="Support on Ko-fi"
        >
            <i class="fa-solid fa-mug-hot"></i>
        </a>
        <a
            href="/downloads/Glacier-Mod-Manager.exe"
            download
            class="header-cta"
        >
            <i class="fa-solid fa-download"></i>
            <span>DOWNLOAD</span>
        </a>
    </div>
</header>

<main>
    <div
        class="content-placeholder"
        in:fly={{ y: 20, duration: 1000, delay: 200, easing: cubicOut }}
    >
        <h1>Frequently Asked Questions</h1>
        <p class="intro">
            Got questions? We've got answers. If you can't find what you're
            looking for here, check out our
            <a href="https://github.com/BySnowden/Glacier" class="text-link"
                >GitHub repository</a
            >.
        </p>

        <div class="faq-container">
            <details class="faq-card">
                <summary>
                    <span class="question">What does Glacier actually do?</span>
                    <i class="fa-solid fa-chevron-down arrow"></i>
                </summary>
                <div class="answer">
                    <p>
                        Glacier scans your Minecraft mods folder to
                        automatically detect incompatible mods, missing
                        dependencies, and version mismatches. Instead of
                        crashing your game and reading cryptic logs for 20
                        minutes, Glacier tells you exactly what is wrong and
                        provides direct links to fix it.
                    </p>
                </div>
            </details>

            <details class="faq-card">
                <summary>
                    <span class="question"
                        >Does it support Fabric, Forge, and NeoForge?</span
                    >
                    <i class="fa-solid fa-chevron-down arrow"></i>
                </summary>
                <div class="answer">
                    <p>
                        Yes! Glacier parses the internal metadata of <code
                            >.jar</code
                        >
                        files, so it works with all major mod loaders including
                        <strong>Fabric</strong>, <strong>Forge</strong>,
                        <strong>NeoForge</strong>, and <strong>Quilt</strong>.
                    </p>
                </div>
            </details>

            <details class="faq-card">
                <summary>
                    <span class="question"
                        >Why does Windows say "Unrecognized App" when I run it?</span
                    >
                    <i class="fa-solid fa-chevron-down arrow"></i>
                </summary>
                <div class="answer">
                    <p>
                        This is a standard warning from Windows SmartScreen for
                        new software that hasn't purchased an expensive "Code
                        Signing Certificate" yet.
                    </p>
                    <p>
                        Glacier is 100% safe and open source. You can click <strong
                            >"More Info"</strong
                        >
                        &rarr; <strong>"Run Anyway"</strong> to start the app. If
                        you are worried, you are welcome to build the app from source
                        code on our GitHub!
                    </p>
                </div>
            </details>

            <details class="faq-card">
                <summary>
                    <span class="question"
                        >Is there a Mac or Linux version?</span
                    >
                    <i class="fa-solid fa-chevron-down arrow"></i>
                </summary>
                <div class="answer">
                    <p>
                        Currently, Glacier is optimized for <strong
                            >Windows</strong
                        >. However, since the app is built with Go and Svelte,
                        Linux and MacOS support is planned for the future. Stay
                        tuned to our GitHub for updates.
                    </p>
                </div>
            </details>

            <details class="faq-card">
                <summary>
                    <span class="question"
                        >Where does it get mod data from?</span
                    >
                    <i class="fa-solid fa-chevron-down arrow"></i>
                </summary>
                <div class="answer">
                    <p>
                        Glacier connects directly to the official <strong
                            >Modrinth</strong
                        >
                        and <strong>CurseForge</strong> APIs to check for updates
                        and fetch mod descriptions. We do not host any mod files ourselves.
                    </p>
                </div>
            </details>

            <details class="faq-card">
                <summary>
                    <span class="question"
                        >I found a bug! Where do I report it?</span
                    >
                    <i class="fa-solid fa-chevron-down arrow"></i>
                </summary>
                <div class="answer">
                    <p>
                        First of all, thank you! Please open an issue on our
                        <a
                            href="https://github.com/BySnowden/Glacier/issues"
                            target="_blank">GitHub Issues page</a
                        >. Include your app version and a screenshot of the
                        error if possible.
                    </p>
                </div>
            </details>
        </div>
    </div>
</main>

<footer>
    <div class="footer-columns">
        <div class="col">
            <h4>Resources</h4>
            <a href="/faq">FAQ</a>
            <a href="https://github.com/BySnowden/Glacier">GitHub</a>
            <a
                href="https://github.com/BySnowden/Glacier?tab=readme-ov-file#%EF%B8%8F-local-development"
                >Documentation</a
            >
        </div>
        <div class="col">
            <h4>Community</h4>
            <a href="https://twitter.com"
                ><i class="fa-brands fa-twitter"></i> Twitter / X</a
            >
            <a href="https://www.youtube.com/@BySnowden"
                ><i class="fa-brands fa-youtube"></i> YouTube</a
            >
        </div>
        <div class="col">
            <h4>Legal</h4>
            <a href="/privacy">Privacy Policy</a>
            <a href="/terms">Terms of Service</a>
            <p class="copyright">© 2026 GLACIER MOD MANAGER</p>
            <p class="disclaimer">Not affiliated with Mojang or Microsoft</p>
        </div>
    </div>

    <div class="footer-cta reveal" use:viewport>
        <h3>Ready to stop wasting time?</h3>
        <a
            href="/downloads/Glacier-Mod-Manager.exe"
            download
            class="primary-3d shimmer-btn"
        >
            <i class="fa-solid fa-download"></i>
            <span>Download Now</span>
        </a>
    </div>
</footer>

<style>
    /* GLOBAL & RESET */
    :global(body) {
        margin: 0;
        font-family: "Inter", sans-serif;
        background-color: #0f172a;
        color: white;
        overflow-x: hidden;
    }

    h1,
    h3,
    h4,
    .logo-text {
        font-family: "Outfit", sans-serif;
    }

    /* BACKGROUND STYLES */
    .background-container {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        z-index: -1;
    }

    .bg-layer {
        position: absolute;
        inset: 0;
        transition: opacity 0.1s linear;
    }

    .bright-layer {
        background: linear-gradient(
            180deg,
            #0f172a 0%,
            #1e3a8a 40%,
            #1e40af 70%,
            #1d4ed8 100%
        );
        z-index: 1;
    }

    .dark-layer {
        background: linear-gradient(
            180deg,
            #0f172a 0%,
            #0f172a 40%,
            #172554 100%
        );
        z-index: 0;
    }

    .grid-pattern {
        position: absolute;
        inset: 0;
        z-index: 2;
        opacity: 0.1;
        background-image:
            linear-gradient(rgba(255, 255, 255, 0.1) 1px, transparent 1px),
            linear-gradient(
                90deg,
                rgba(255, 255, 255, 0.1) 1px,
                transparent 1px
            );
        background-size: 50px 50px;
        animation: gridDrift 20s linear infinite;
    }

    @keyframes gridDrift {
        0% {
            background-position: 0 0;
        }
        100% {
            background-position: 50px 50px;
        }
    }

    /* HEADER STYLES */
    header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 1.25rem 2rem;
        border-bottom: 2px solid rgba(59, 130, 246, 0.3);
        background-color: rgba(15, 23, 42, 0.8);
        backdrop-filter: blur(8px);
        position: sticky;
        top: 0;
        z-index: 100;
    }

    .logo-container {
        display: flex;
        align-items: center;
        gap: 0.75rem;
    }

    .logo-text-link {
        text-decoration: none;
        color: white;
    }

    .logo-box {
        width: 40px;
        height: 40px;
        display: flex;
        align-items: center;
        justify-content: center;
        border-radius: 8px;
    }

    .logo-icon {
        width: 100%;
        height: 100%;
        object-fit: contain;
    }

    .logo-text {
        font-weight: 900;
        font-size: 1.25rem;
        letter-spacing: 0.05em;
    }

    .nav-buttons {
        display: flex;
        align-items: center;
        gap: 1rem;
    }

    .icon-link {
        color: #94a3b8;
        font-size: 1.25rem;
        transition: color 0.2s;
    }

    .icon-link:hover {
        color: white;
    }

    .header-cta {
        background-color: #2563eb;
        color: white;
        border: none;
        border-bottom: 4px solid #1e40af;
        padding: 0.5rem 1rem;
        font-weight: 700;
        border-radius: 4px;
        cursor: pointer;
        display: flex;
        align-items: center;
        gap: 0.5rem;
        text-decoration: none;
        transition:
            transform 0.1s,
            border 0.1s;
    }

    .header-cta:active {
        border-bottom-width: 0;
        transform: translateY(4px);
    }

    /* MAIN CONTENT AREA */
    main {
        max-width: 800px; /* Reduced width for readability of text pages */
        margin: 0 auto;
        padding: 8rem 1.5rem 5rem 1.5rem;
        min-height: 60vh; /* Ensures footer stays down even with little content */
    }

    .content-placeholder h1 {
        font-size: 3.5rem;
        margin-bottom: 2rem;
        text-align: center;
        background: linear-gradient(135deg, #00d4ff 0%, #0099cc 100%);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        background-clip: text;
        position: relative;
    }

    .content-placeholder h1::after {
        content: "";
        position: absolute;
        bottom: -10px;
        left: 50%;
        transform: translateX(-50%);
        width: 80px;
        height: 3px;
        background: linear-gradient(90deg, #00d4ff, #0099cc);
        border-radius: 2px;
    }

    /* FOOTER STYLES */
    footer {
        background-color: #020617;
        border-top: 1px solid rgba(59, 130, 246, 0.2);
        padding: 4rem 1.5rem;
    }

    .footer-columns {
        max-width: 1200px;
        margin: 0 auto;
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
        gap: 3rem;
        margin-bottom: 4rem;
    }

    .col h4 {
        color: white;
        text-transform: uppercase;
        margin-bottom: 1.5rem;
        font-size: 1.1rem;
    }

    .col a {
        display: block;
        color: #94a3b8;
        text-decoration: none;
        margin-bottom: 0.75rem;
        font-weight: 500;
        transition: color 0.2s;
    }

    .col a:hover {
        color: #3b82f6;
    }

    .copyright,
    .disclaimer {
        color: #475569;
        font-size: 0.875rem;
        margin-top: 1rem;
    }

    .footer-cta {
        text-align: center;
        border-top: 2px solid #1e293b;
        padding-top: 3rem;
        max-width: 600px;
        margin: 0 auto;
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .footer-cta h3 {
        margin-bottom: 2rem;
        font-size: 1.5rem;
        text-transform: uppercase;
    }

    .primary-3d {
        background-color: #2563eb;
        color: white;
        border: none;
        border-bottom: 5px solid #1d4ed8;
        padding: 1rem 2rem;
        font-size: 1.1rem;
        font-weight: 800;
        text-transform: uppercase;
        border-radius: 6px;
        cursor: pointer;
        display: flex;
        align-items: center;
        gap: 0.75rem;
        transition: all 0.1s;
        text-decoration: none;
    }

    .primary-3d:active {
        transform: translateY(5px);
        border-bottom-width: 0;
    }

    .shimmer-btn {
        position: relative;
        overflow: hidden;
    }

    .shimmer-btn::after {
        content: "";
        position: absolute;
        top: 0;
        left: -100%;
        width: 100%;
        height: 100%;
        background: linear-gradient(
            90deg,
            transparent,
            rgba(255, 255, 255, 0.2),
            transparent
        );
        transition: 0.5s;
        animation: shimmer 3s infinite;
    }

    @keyframes shimmer {
        0% {
            left: -100%;
        }
        20% {
            left: 100%;
        }
        100% {
            left: 100%;
        }
    }

    /* REVEAL UTILS (Kept for Footer) */
    .reveal {
        opacity: 0;
        transform: translateY(30px) scale(0.98);
        transition:
            opacity 0.8s cubic-bezier(0.16, 1, 0.3, 1),
            transform 0.8s cubic-bezier(0.16, 1, 0.3, 1);
        will-change: transform, opacity;
    }

    :global(.reveal.visible) {
        opacity: 1;
        transform: translateY(0) scale(1);
    }

    /* --- FAQ SPECIFIC STYLES --- */

    .intro {
        font-size: 1.2rem;
        line-height: 1.7;
        margin-bottom: 4rem;
        color: #e2e8f0;
        text-align: center;
        max-width: 600px;
        margin-left: auto;
        margin-right: auto;
        opacity: 0.9;
        font-weight: 400;
    }

    .text-link {
        color: #38bdf8;
        text-decoration: none;
        border-bottom: 1px solid rgba(56, 189, 248, 0.3);
        transition: all 0.2s;
    }

    .text-link:hover {
        border-bottom-color: #38bdf8;
        color: #60a5fa;
    }

    .faq-container {
        display: flex;
        flex-direction: column;
        gap: 2rem;
        max-width: 800px;
        margin: 0 auto;
        padding: 0 1rem;
    }

    /* The Accordion Card */
    .faq-card {
        background: rgba(255, 255, 255, 0.05);
        border: 1px solid rgba(255, 255, 255, 0.12);
        border-radius: 16px;
        backdrop-filter: blur(15px);
        transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
        box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
        position: relative;
        overflow: hidden;
    }

    .faq-card::before {
        content: "";
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        height: 1px;
        background: linear-gradient(
            90deg,
            transparent,
            rgba(0, 212, 255, 0.5),
            transparent
        );
        opacity: 0;
        transition: opacity 0.3s ease;
    }

    .faq-card:hover {
        border-color: rgba(59, 130, 246, 0.5);
        background: rgba(255, 255, 255, 0.05);
    }

    /* Open State Styling */
    .faq-card[open] {
        border-color: #38bdf8;
        background: rgba(15, 23, 42, 0.6);
    }

    /* The Clickable Header */
    summary {
        padding: 1.5rem;
        cursor: pointer;
        display: flex;
        justify-content: space-between;
        align-items: center;
        list-style: none; /* Hides default triangle */
        user-select: none;
    }

    /* Hide default marker in Webkit */
    summary::-webkit-details-marker {
        display: none;
    }

    .question {
        font-family: "Outfit", sans-serif;
        font-weight: 700;
        font-size: 1.1rem;
        color: white;
    }

    .arrow {
        color: #38bdf8;
        transition: transform 0.3s ease;
    }

    /* Rotate arrow when open */
    details[open] summary .arrow {
        transform: rotate(180deg);
        color: #00d4ff;
    }

    /* The Content inside */
    .answer {
        padding: 0 1.5rem 1.5rem 1.5rem;
        line-height: 1.6;
        color: #cbd5e1;
        border-top: 1px solid rgba(255, 255, 255, 0.05);
        margin-top: -0.5rem; /* Pull closer to header */
        padding-top: 1rem;
    }

    .answer p {
        margin: 0;
        margin-bottom: 1rem;
    }

    .answer p:last-child {
        margin-bottom: 0;
    }

    .answer a {
        color: #00d4ff;
        text-decoration: none;
        border-bottom: 1px solid rgba(0, 212, 255, 0.3);
        transition: all 0.3s ease;
        font-weight: 500;
    }

    .answer a:hover {
        color: #60a5fa;
        border-bottom-color: #60a5fa;
        transform: translateY(-1px);
    }

    .answer code {
        background: rgba(0, 0, 0, 0.3);
        padding: 2px 6px;
        border-radius: 4px;
        font-family: monospace;
        color: #e2e8f0;
    }

    @media (max-width: 768px) {
        .logo-text {
            display: none;
        }
        main {
            padding: 2rem 1rem;
        }
        .content-placeholder h1 {
            font-size: 2.5rem;
            margin-bottom: 1.5rem;
        }
        .content-placeholder h1::after {
            width: 60px;
            height: 2px;
        }
        .intro {
            font-size: 1.1rem;
            margin-bottom: 3rem;
            padding: 0 1rem;
        }
        .faq-container {
            gap: 1.5rem;
            padding: 0 0.5rem;
        }
        summary {
            padding: 1.5rem;
            font-size: 1.1rem;
        }
        summary:hover {
            padding-left: 2rem;
        }
        .answer {
            padding: 0 1.5rem 1.5rem;
            font-size: 1rem;
        }
    }
</style>
