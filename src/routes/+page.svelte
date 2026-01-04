<script lang="ts">
    import { fly } from "svelte/transition";
    import { cubicOut } from "svelte/easing";

    let y = 0;

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

    const flyConfig = { y: 20, duration: 1000, easing: cubicOut };
</script>

<svelte:window bind:scrollY={y} />

<svelte:head>
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
        <span class="logo-text">GLACIER</span>
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
    <section class="hero">
        <div class="badge" in:fly={{ ...flyConfig, delay: 200 }}>
            <i class="fa-solid fa-cube"></i>
            <span>Minecraft Java Edition</span>
        </div>

        <h1 in:fly={{ ...flyConfig, delay: 400 }}>Glacier Mod Manager</h1>

        <p class="subtitle" in:fly={{ ...flyConfig, delay: 500 }}>
            Stop wasting 30 minutes debugging mod conflicts.
        </p>

        <p class="description" in:fly={{ ...flyConfig, delay: 600 }}>
            Automatically detects incompatibilities, version mismatches, and
            missing dependencies. Know exactly what's conflicting—and what to
            download instead.
        </p>

        <div class="button-row" in:fly={{ ...flyConfig, delay: 700 }}>
            <a
                href="/downloads/Glacier-Mod-Manager.exe"
                download
                class="primary-3d shimmer-btn"
            >
                <i class="fa-solid fa-download"></i>
                <span>Download for Windows</span>
            </a>
            <a
                href="https://github.com/BySnowden/Glacier"
                target="_blank"
                class="secondary-3d"
            >
                <i class="fa-brands fa-github"></i>
                <span>View on GitHub</span>
            </a>
        </div>
    </section>

    <section class="showcase-container reveal" use:viewport>
        <div class="window-frame">
            <div class="window-header">
                <div class="dot red"></div>
                <div class="dot yellow"></div>
                <div class="dot green"></div>
            </div>
            <img
                src="/images/filled-showcase-light.png"
                alt="Glacier Mod Manager Interface"
                class="app-screenshot"
            />
        </div>
    </section>

    <section class="comparison-grid">
        <div class="card problem reveal" use:viewport>
            <div class="card-icon red-bg">
                <i class="fa-solid fa-triangle-exclamation"></i>
            </div>
            <div class="card-text">
                <h3>The Problem</h3>
                <p>
                    Game crashes. Check logs. Google error messages. Try
                    different versions. Repeat for hours.
                </p>
                <span class="impact red-text"
                    >30+ MINUTES WASTED EVERY TIME</span
                >
            </div>
        </div>

        <div
            class="card solution reveal"
            use:viewport
            style="transition-delay: 200ms"
        >
            <div class="card-icon green-bg">
                <i class="fa-solid fa-bolt"></i>
            </div>
            <div class="card-text">
                <h3>The Solution</h3>
                <p>
                    Instant conflict detection. Clear explanations. Suggested
                    fixes. One-click resolution.
                </p>
                <span class="impact green-text">FIXED IN SECONDS</span>
            </div>
        </div>
    </section>

    <section class="features-grid">
        <div class="feature-card reveal" use:viewport>
            <div class="feature-icon">
                <i class="fa-solid fa-shield-halved"></i>
            </div>
            <h3>Smart Detection</h3>
            <p>
                Scans all mods instantly to find version conflicts, missing
                dependencies, and incompatible combinations.
            </p>
        </div>

        <div
            class="feature-card reveal"
            use:viewport
            style="transition-delay: 150ms"
        >
            <div class="feature-icon">
                <i class="fa-solid fa-wand-magic-sparkles"></i>
            </div>
            <h3>One-Click Fixes</h3>
            <p>
                Get clear suggestions for which versions to use or which
                alternatives to download. No more guesswork.
            </p>
        </div>

        <div
            class="feature-card reveal"
            use:viewport
            style="transition-delay: 300ms"
        >
            <div class="feature-icon">
                <i class="fa-solid fa-code-branch"></i>
            </div>
            <h3>Open Source</h3>
            <p>
                Built by the community, for the community. Completely free,
                transparent, and always improving on GitHub.
            </p>
        </div>
    </section>
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
    .logo-text,
    .badge {
        font-family: "Outfit", sans-serif;
    }

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

    /* DARK LAYER (Revealed on scroll):
       Uses your dark palette: #172554 (Deep Blue)
    */
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

    main {
        max-width: 1200px;
        margin: 0 auto;
        padding: 5rem 1.5rem;
        display: flex;
        flex-direction: column;
        align-items: center;
        text-align: center;
    }

    .badge {
        display: inline-flex;
        align-items: center;
        gap: 0.5rem;
        background-color: rgba(30, 41, 59, 0.9);
        border-left: 4px solid #3b82f6;
        padding: 0.5rem 1rem;
        margin-bottom: 2rem;
        text-transform: uppercase;
        font-weight: 600;
        font-size: 0.85rem;
        letter-spacing: 0.05em;
    }

    h1 {
        font-size: 4.5rem;
        font-weight: 900;
        margin: 0 0 1.5rem 0;
        text-transform: uppercase;
        line-height: 1;
        letter-spacing: -0.02em;
    }

    .subtitle {
        font-size: 1.5rem;
        color: #e2e8f0;
        margin-bottom: 1rem;
        font-weight: 600;
    }

    .description {
        font-size: 1.125rem;
        color: #94a3b8;
        max-width: 700px;
        line-height: 1.6;
        margin-bottom: 3rem;
    }

    .button-row {
        display: flex;
        gap: 1.5rem;
        margin-bottom: 6rem;
        flex-wrap: wrap;
        justify-content: center;
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

    .secondary-3d {
        background-color: #1e293b;
        color: white;
        border: 2px solid #475569;
        border-bottom: 5px solid #475569;
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

    .secondary-3d:active {
        transform: translateY(5px);
        border-bottom-width: 2px;
    }

    .showcase-container {
        width: 100%;
        display: flex;
        justify-content: center;
        margin-top: 3rem;
        margin-bottom: 8rem;
        padding: 0 1.5rem;
        perspective: 1000px;
    }

    .window-frame {
        background-color: #1e293b;
        padding: 10px 10px 0 10px;
        border-radius: 12px;
        box-shadow:
            0 50px 100px -20px rgba(0, 0, 0, 0.7),
            0 0 80px -20px rgba(37, 99, 235, 0.3);
        border: 1px solid rgba(255, 255, 255, 0.1);
        max-width: 1100px;
        width: 100%;
        overflow: hidden;
        position: relative;
    }

    .window-frame::after {
        content: "";
        position: absolute;
        bottom: 0;
        left: 0;
        width: 100%;
        height: 150px;
        background: linear-gradient(
            to bottom,
            transparent,
            rgba(15, 23, 42, 0.1)
        );
        pointer-events: none;
    }

    .window-header {
        display: flex;
        gap: 8px;
        margin-bottom: 10px;
        padding-left: 6px;
    }

    .dot {
        width: 10px;
        height: 10px;
        border-radius: 50%;
    }
    .red {
        background-color: #ef4444;
    }
    .yellow {
        background-color: #eab308;
    }
    .green {
        background-color: #22c55e;
    }

    .app-screenshot {
        width: 100%;
        height: auto;
        display: block;
        border-top-left-radius: 8px;
        border-top-right-radius: 8px;
    }

    .comparison-grid {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 2rem;
        width: 100%;
        margin-bottom: 6rem;
    }

    .card {
        background-color: rgba(15, 23, 42, 0.8);
        padding: 2rem;
        border-left: 4px solid;
        display: flex;
        gap: 1.5rem;
        text-align: left;
    }

    .problem {
        border-color: #ef4444;
    }
    .solution {
        border-color: #10b981;
    }

    .card-icon {
        width: 3rem;
        height: 3rem;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 1.5rem;
        flex-shrink: 0;
        border-radius: 4px;
    }

    .red-bg {
        background-color: rgba(127, 29, 29, 0.5);
        color: #f87171;
    }
    .green-bg {
        background-color: rgba(6, 78, 59, 0.5);
        color: #34d399;
    }

    .card-text h3 {
        margin: 0 0 0.5rem 0;
        font-size: 1.5rem;
        text-transform: uppercase;
    }

    .card-text p {
        color: #cbd5e1;
        line-height: 1.5;
        margin-bottom: 1rem;
    }

    .impact {
        font-weight: 800;
        font-size: 0.875rem;
        letter-spacing: 0.05em;
    }
    .red-text {
        color: #f87171;
    }
    .green-text {
        color: #34d399;
    }

    .features-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
        gap: 1.5rem;
        width: 100%;
    }

    .feature-card {
        background-color: rgba(15, 23, 42, 0.6);
        border: 2px solid #334155;
        padding: 2rem;
        text-align: left;
    }

    .feature-card:hover {
        border-color: #3b82f6;
        transform: translateY(-2px);
        box-shadow: 0 10px 30px -10px rgba(0, 0, 0, 0.5);
    }

    .feature-icon {
        width: 4rem;
        height: 4rem;
        background-color: #2563eb;
        color: white;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 1.75rem;
        margin-bottom: 1.5rem;
    }

    .feature-card h3 {
        font-size: 1.25rem;
        margin-bottom: 1rem;
        text-transform: uppercase;
    }

    .feature-card p {
        color: #94a3b8;
        line-height: 1.6;
    }

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

    @media (max-width: 768px) {
        h1 {
            font-size: 3rem;
        }
        .comparison-grid {
            grid-template-columns: 1fr;
        }
        .logo-text {
            display: none;
        }
    }
</style>
