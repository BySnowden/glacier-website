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
    <title>Terms of Service - Glacier Mod Manager</title>
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
        <h1>Terms of Service</h1>
        <p class="last-updated">Last updated: January 04, 2026</p>

        <p class="intro">
            By downloading or using Glacier Mod Manager ("Software"), you agree
            to be bound by these Terms of Service. If you do not agree to these
            terms, please do not use the Software.
        </p>

        <div class="policy-stack">
            <section class="policy-card">
                <h2>1. Open Source License</h2>
                <p>
                    Glacier is free and open-source software distributed under
                    the <strong
                        >GNU General Public License v3.0 (GPL-3.0)</strong
                    >.
                </p>
                <p>
                    You are free to use, modify, and distribute the Software,
                    provided that any modifications or derivative works are also
                    licensed under the GPL-3.0 and remain open source.
                </p>
                <p>
                    You can review the full license text and source code on our
                    GitHub repository:
                </p>
                <p>
                    <a
                        href="https://github.com/BySnowden/Glacier"
                        target="_blank">github.com/BySnowden/Glacier</a
                    >
                </p>
            </section>

            <section class="policy-card">
                <h2>2. User Responsibility & Risk</h2>
                <p>
                    Glacier is a tool designed to manage files on your computer.
                    While we take every precaution to ensure safety:
                </p>
                <ul>
                    <li>
                        You acknowledge that modifying game files always carries
                        a risk of data loss or save corruption.
                    </li>
                    <li>
                        We strongly recommend backing up your <code
                            >.minecraft</code
                        > folder or world saves before using this tool.
                    </li>
                    <li>
                        We are not responsible for any issues that arise from
                        incompatible mods, version mismatches, or user error.
                    </li>
                </ul>
            </section>

            <section class="policy-card">
                <h2>3. Disclaimer of Warranty</h2>
                <p class="uppercase-legal">
                    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY
                    KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE
                    WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR
                    PURPOSE AND NONINFRINGEMENT. THE ENTIRE RISK AS TO THE
                    QUALITY AND PERFORMANCE OF THE SOFTWARE IS WITH YOU.
                </p>
            </section>

            <section class="policy-card">
                <h2>4. Limitation of Liability</h2>
                <p class="uppercase-legal">
                    IN NO EVENT SHALL THE DEVELOPERS OR COPYRIGHT HOLDERS BE
                    LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN
                    AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT
                    OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER
                    DEALINGS IN THE SOFTWARE.
                </p>
            </section>

            <section class="policy-card">
                <h2>5. Donations & Tips</h2>
                <p>
                    If you choose to support the development of Glacier via
                    Ko-fi or other platforms ("Tips"), you acknowledge that:
                </p>
                <ul>
                    <li>
                        Tips are voluntary gifts and do not constitute a
                        purchase of goods or services.
                    </li>
                    <li>Tips are non-refundable.</li>
                    <li>
                        Donating does not grant you any special rights,
                        ownership, or say in the direction of the project.
                    </li>
                </ul>
            </section>

            <section class="policy-card">
                <h2>6. Third-Party Content</h2>
                <p>
                    Glacier may display content from third-party sources (such
                    as Modrinth or CurseForge). We do not own, control, or
                    endorse the mods available through these services. You are
                    subject to the Terms of Service of those respective
                    platforms when downloading content.
                </p>
            </section>

            <section class="policy-card">
                <h2>7. Best Practices for Safety</h2>
                <p>
                    To ensure the best experience and protect your data, we
                    strongly recommend the following "safety first" approach
                    when modding:
                </p>
                <ul class="safety-list">
                    <li>
                        <i class="fa-solid fa-floppy-disk"></i>
                        <strong>Backup Often:</strong> Always create a backup of
                        your <code>.minecraft/saves</code> folder before trying new
                        mod combinations.
                    </li>
                    <li>
                        <i class="fa-solid fa-vial"></i>
                        <strong>Test in New Worlds:</strong> When testing a new modpack
                        detected by Glacier, try loading into a "Creative" test world
                        first to ensure stability before opening your main survival
                        world.
                    </li>
                    <li>
                        <i class="fa-solid fa-circle-info"></i>
                        <strong>Read the Logs:</strong> Glacier provides detailed
                        conflict info; if the app suggests a version is incompatible,
                        take that warning seriously to avoid world corruption.
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
        background: linear-gradient(135deg, #00d4ff 0%, #0099cc 100%);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        background-clip: text;
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

    /* --- TERMS OF SERVICE CONTENT STYLES --- */

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
        max-width: 700px;
    }

    .policy-stack {
        display: flex;
        flex-direction: column;
        gap: 2rem;
        text-align: left;
    }

    /* Card Styling (Glassmorphism) */
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
        font-family: "Outfit", sans-serif;
        font-size: 1.5rem;
        margin-top: 0;
        margin-bottom: 1rem;
        color: #38bdf8; /* Glacier Blue */
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

    /* Links: White by default, Blue on hover */
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

    /* LEGAL DISCLAIMERS (Sections 3 & 4) */
    .uppercase-legal {
        text-transform: uppercase;
        font-size: 0.9rem;
        letter-spacing: 0.05em;
        opacity: 0.9;
        line-height: 1.7;
        font-weight: 500;
        background: rgba(0, 0, 0, 0.3); /* Darker background for contrast */
        padding: 1.5rem;
        border-radius: 8px;
        border-left: 3px solid #64748b; /* Grey bar to signify 'legal' */
        color: #e2e8f0;
    }

    /* SAFETY LIST (Section 7) */
    .safety-list {
        list-style: none;
        margin-left: 0 !important;
        padding: 0;
    }

    .safety-list li {
        display: flex;
        align-items: flex-start;
        gap: 1rem;
        margin-bottom: 1rem;
        padding: 1rem;
        background: rgba(56, 189, 248, 0.05); /* Subtle blue tint */
        border-radius: 8px;
        border-left: 3px solid #38bdf8;
    }

    .safety-list i {
        color: #38bdf8;
        margin-top: 0.3rem;
        font-size: 1.1rem;
        flex-shrink: 0;
    }

    .safety-list strong {
        display: block;
        color: #fff;
        margin-bottom: 0.25rem;
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
