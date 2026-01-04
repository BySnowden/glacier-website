<script lang="ts">
    import { fly } from "svelte/transition";
    import { cubicOut } from "svelte/easing";

    let y = 0;

    // Logic to fade the background layer based on scroll, just like the home page
    $: brightOpacity = Math.max(0, 1 - y / 500);

    // Kept the viewport action in case you want to use the reveal animations
    // for your privacy text paragraphs later, or for the footer which uses it.
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
    <title>Privacy Policy - Glacier Mod Manager</title>
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
        <h1>Privacy Policy</h1>
        <p class="last-updated">Version 1.2 - Last updated: January 4, 2026</p>

        <p class="intro">
            Glacier Mod Manager ("Glacier", "We", "Us") is a desktop application
            designed to run locally on your device. We respect your privacy and
            are committed to protecting it. This Privacy Policy explains our
            practices regarding your data.
        </p>

        <div class="policy-stack">
            <section class="policy-card">
                <h2>1. Privacy by Design</h2>
                <p class="highlight">
                    We do not collect, store, or transmit any personal data.
                </p>
                <p>Glacier is built with privacy as a core principle:</p>
                <ul>
                    <li>We do not have user accounts or login systems</li>
                    <li>
                        We do not collect your IP address or usage analytics
                    </li>
                    <li>We do not use cookies or tracking technologies</li>
                    <li>
                        <strong>Our code is open source</strong> - you can verify
                        our privacy claims yourself
                    </li>
                </ul>
                <p class="highlight">
                    <i class="fa-brands fa-github"></i>
                    <a
                        href="https://github.com/BySnowden/Glacier"
                        target="_blank">Review our source code on GitHub</a
                    >
                </p>
            </section>

            <section class="policy-card">
                <h2>2. Local Data Processing</h2>
                <p>
                    Glacier functions by scanning and managing the files located
                    on your own computer (specifically within your Minecraft
                    directory). All processing of file metadata, dependency
                    checks, and version comparisons happens strictly on your
                    local device.
                </p>
                <p class="highlight">
                    No information about your files is ever uploaded to our
                    servers.
                </p>
            </section>

            <section class="policy-card">
                <h2>3. Network Communication</h2>
                <p>
                    Glacier connects to external services only when you
                    explicitly request certain actions.
                    <strong>No background data transmission occurs.</strong> Network
                    requests happen only when you:
                </p>
                <ul>
                    <li>Search for mods or check for updates</li>
                    <li>Download mod files</li>
                    <li>Check for Glacier application updates</li>
                    <li>Visit linked external resources</li>
                </ul>
                <p>
                    During these interactions, external services may see your IP
                    address as part of standard web communication. We do not
                    share your personal data with these providers.
                </p>
                <ul class="provider-list">
                    <li>
                        <strong>Modrinth & CurseForge:</strong> Used to fetch
                        mod metadata, check for updates, and download mod files.
                        <br />
                        <a
                            href="https://docs.modrinth.com/legal/privacy"
                            target="_blank">Modrinth Privacy</a
                        >
                        •
                        <a
                            href="https://www.overwolf.com/legal/privacy"
                            target="_blank">CurseForge Privacy</a
                        >
                    </li>
                    <li>
                        <strong>GitHub:</strong> Used to host the Glacier source
                        code, manage issue tracking, and distribute software
                        updates.
                        <br />
                        <a
                            href="https://docs.github.com/en/site-policy/privacy-policies/github-general-privacy-statement"
                            target="_blank">GitHub Privacy Statement</a
                        >
                    </li>
                    <li>
                        <strong>Ko-fi:</strong> Used for optional donations. If
                        you choose to support development, your payment info is
                        processed entirely by Ko-fi; Glacier never sees your
                        financial details.
                        <br />
                        <a href="https://more.ko-fi.com/privacy" target="_blank"
                            >Ko-fi Privacy Policy</a
                        >
                    </li>
                </ul>
            </section>

            <section class="policy-card">
                <h2>4. Local Data Storage</h2>
                <p>
                    Glacier may store temporary files and cache data on your
                    local device to improve performance. This includes:
                </p>
                <ul>
                    <li>Cached mod metadata for faster loading</li>
                    <li>Application preferences and settings</li>
                    <li>Downloaded mod files (managed by you)</li>
                </ul>
                <p class="highlight">
                    All stored data remains on your device and can be cleared
                    through the application settings or by uninstalling Glacier.
                </p>
            </section>

            <section class="policy-card">
                <h2>5. Security</h2>
                <p>
                    While we don't handle your personal data, we take security
                    seriously:
                </p>
                <ul>
                    <li>All downloads are verified for integrity</li>
                    <li>
                        Connections to external services use HTTPS encryption
                    </li>
                    <li>No sensitive data is stored or transmitted</li>
                </ul>
            </section>

            <section class="policy-card">
                <h2>6. Your Rights</h2>
                <p>
                    Since we don't collect your personal data, traditional data
                    rights don't apply. However, you maintain complete control
                    over:
                </p>
                <ul>
                    <li>
                        <strong>Usage:</strong> You can stop using Glacier at any
                        time
                    </li>
                    <li>
                        <strong>Data:</strong> You can delete all Glacier files and
                        settings from your device
                    </li>
                    <li>
                        <strong>Network:</strong> You can use Glacier offline for
                        local mod management
                    </li>
                    <li>
                        <strong>Transparency:</strong> Our source code is publicly
                        available for review
                    </li>
                </ul>
            </section>

            <section class="policy-card">
                <h2>7. Children's Privacy</h2>
                <p>
                    Glacier is safe for users of all ages since we don't collect
                    any personal information from anyone, including children
                    under 13.
                </p>
            </section>

            <section class="policy-card">
                <h2>8. Changes to This Policy</h2>
                <p>
                    We may update our Privacy Policy from time to time. Thus,
                    you are advised to review this page periodically for any
                    changes. We will notify you of any changes by posting the
                    new Privacy Policy on this page.
                </p>
            </section>

            <section class="policy-card">
                <h2>9. Contact Us</h2>
                <p>
                    If you have any questions or suggestions about our Privacy
                    Policy, do not hesitate to contact us:
                </p>
                <ul class="contact-list">
                    <li>
                        <i class="fa-solid fa-envelope"></i>
                        <strong>Email:</strong>
                        <a href="mailto:bysnowden.dev@gmail.com"
                            >bysnowden.dev@gmail.com</a
                        >
                    </li>
                    <li>
                        <i class="fa-brands fa-github"></i>
                        <strong>GitHub Issues:</strong>
                        <a
                            href="https://github.com/BySnowden/Glacier/issues"
                            target="_blank"
                            rel="noopener noreferrer"
                            >github.com/BySnowden/Glacier/issues</a
                        >
                    </li>
                </ul>
            </section>
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
    /* --- GLOBAL & RESET --- */
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
    .policy-card h2 {
        font-family: "Outfit", sans-serif;
    }

    /* --- BACKGROUND STYLES --- */
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

    /* --- HEADER STYLES --- */
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

    /* --- MAIN CONTENT & PRIVACY SPECIFIC STYLES --- */
    main {
        max-width: 800px;
        margin: 0 auto;
        padding: 8rem 1.5rem 5rem 1.5rem;
        min-height: 60vh;
    }

    .content-placeholder h1 {
        font-size: 3.5rem;
        margin-bottom: 2rem;
        background: linear-gradient(135deg, #00d4ff 0%, #0099cc 100%);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        background-clip: text;
    }

    .last-updated {
        opacity: 0.7;
        font-style: italic;
        margin-bottom: 2rem;
        color: #94a3b8;
    }

    .intro {
        font-size: 1.1rem;
        line-height: 1.6;
        margin-bottom: 3rem;
        color: #e2e8f0;
    }

    .policy-stack {
        display: flex;
        flex-direction: column;
        gap: 2rem;
    }

    /* This is the missing part that gives the cards the glass look */
    .policy-card {
        background: rgba(255, 255, 255, 0.03);
        border: 1px solid rgba(255, 255, 255, 0.1);
        border-radius: 12px;
        padding: 2rem;
        backdrop-filter: blur(10px);
        transition:
            transform 0.2s,
            border-color 0.2s;
    }

    .policy-card:hover {
        border-color: rgba(59, 130, 246, 0.5);
        transform: translateY(-2px);
    }

    .policy-card h2 {
        font-size: 1.5rem;
        margin-top: 0;
        margin-bottom: 1rem;
        color: #38bdf8;
    }

    .policy-card p,
    .policy-card li {
        line-height: 1.6;
        color: #cbd5e1;
        margin-bottom: 1rem;
    }

    .policy-card ul {
        margin-left: 1.5rem;
        margin-bottom: 1rem;
    }

    /* Highlight box for "No Data Collection" */
    .highlight {
        font-weight: 600;
        color: #fff;
        background: rgba(59, 130, 246, 0.1);
        display: inline-block;
        padding: 4px 12px;
        border-radius: 4px;
        border-left: 3px solid #38bdf8;
    }

    /* Link Styles */
    .policy-card a {
        color: #ffffff;
        text-decoration: underline;
        text-decoration-color: rgba(255, 255, 255, 0.3);
        font-weight: 600;
        transition: all 0.2s ease;
    }

    .policy-card a:hover {
        color: #38bdf8;
        text-decoration-color: #38bdf8;
    }

    /* Provider List Styles (Modrinth, etc) */
    .provider-list {
        list-style: none;
        margin-left: 0 !important;
        padding: 0;
    }

    .provider-list li {
        margin-bottom: 1.5rem;
        padding-bottom: 1.5rem;
        border-bottom: 1px solid rgba(255, 255, 255, 0.1);
    }

    .provider-list li:last-child {
        border-bottom: none;
    }

    .provider-list strong {
        color: #e2e8f0;
        font-size: 1.05rem;
        display: block;
        margin-bottom: 0.25rem;
    }

    /* Contact List Styles */
    .contact-list {
        list-style: none;
        margin-left: 0 !important;
        padding: 0;
    }

    .contact-list li {
        display: flex;
        align-items: center;
        gap: 0.75rem;
        margin-bottom: 1rem;
    }

    .contact-list i {
        color: #94a3b8;
    }

    /* --- FOOTER STYLES --- */
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

    @media (max-width: 768px) {
        .logo-text {
            display: none;
        }
        main {
            padding-top: 6rem;
        }
        .content-placeholder h1 {
            font-size: 2.5rem;
        }
    }
</style>
