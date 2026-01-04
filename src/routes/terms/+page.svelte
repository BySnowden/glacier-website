<svelte:head>
    <title>Terms of Service - Glacier Mod Manager</title>
    <meta name="description" content="Terms of service for Glacier Mod Manager" />
</svelte:head>

<div class="terms-container">
    <header class="terms-header">
        <h1>Terms of Service</h1>
        <p>Last updated: January 4, 2025</p>
    </header>

    <main class="terms-content">
        <section class="terms-section">
            <h2>Acceptance of Terms</h2>
            <p>By downloading, installing, or using Glacier Mod Manager, you agree to be bound by these Terms of Service. If you do not agree to these terms, please do not use our software.</p>
        </section>

        <section class="terms-section">
            <h2>Description of Service</h2>
            <p>Glacier Mod Manager is a free, open-source mod management tool designed to help users install, organize, and manage modifications for supported games. The software is provided "as is" without warranty of any kind.</p>
        </section>

        <section class="terms-section">
            <h2>User Responsibilities</h2>
            <h3>Acceptable Use</h3>
            <ul>
                <li>Use Glacier only for legitimate mod management purposes</li>
                <li>Comply with all applicable laws and regulations</li>
                <li>Respect the terms of service of games and mod repositories</li>
                <li>Do not use Glacier to distribute malicious content</li>
            </ul>

            <h3>Game and Mod Compatibility</h3>
            <ul>
                <li>Ensure you own legitimate copies of games you're modding</li>
                <li>Verify mod compatibility and safety before installation</li>
                <li>Back up your game saves and files before modding</li>
            </ul>
        </section>

        <section class="terms-section">
            <h2>Disclaimer of Warranties</h2>
            <p>Glacier Mod Manager is provided on an "as is" and "as available" basis. We make no representations or warranties of any kind, express or implied, regarding:</p>
            <ul>
                <li>The functionality or reliability of the software</li>
                <li>Compatibility with all games, mods, or systems</li>
                <li>Prevention of data loss or system damage</li>
                <li>Continuous availability or error-free operation</li>
            </ul>
        </section>

        <section class="terms-section">
            <h2>Limitation of Liability</h2>
            <p>To the fullest extent permitted by law, the developers of Glacier Mod Manager shall not be liable for any:</p>
            <ul>
                <li>Direct, indirect, incidental, or consequential damages</li>
                <li>Data loss, system damage, or corruption</li>
                <li>Issues arising from third-party mods or content</li>
                <li>Violations of game terms of service by users</li>
            </ul>
        </section>

        <section class="terms-section">
            <h2>Third-Party Content</h2>
            <p>Glacier Mod Manager may facilitate access to third-party mods, repositories, and content. We are not responsible for:</p>
            <ul>
                <li>The quality, safety, or legality of third-party content</li>
                <li>Third-party terms of service or privacy policies</li>
                <li>Disputes between users and third-party content creators</li>
            </ul>
        </section>

        <section class="terms-section">
            <h2>Open Source License</h2>
            <p>Glacier Mod Manager is open-source software. The source code is available on GitHub and is subject to the terms of our open-source license. Users are free to view, modify, and distribute the software according to the license terms.</p>
        </section>

        <section class="terms-section">
            <h2>Modifications to Terms</h2>
            <p>We reserve the right to modify these Terms of Service at any time. Changes will be effective immediately upon posting. Continued use of Glacier after changes constitutes acceptance of the new terms.</p>
        </section>

        <section class="terms-section">
            <h2>Termination</h2>
            <p>You may stop using Glacier Mod Manager at any time by uninstalling the software. These terms will survive termination where applicable.</p>
        </section>

        <section class="terms-section">
            <h2>Contact Information</h2>
            <p>For questions about these Terms of Service, please contact us through our GitHub repository or community channels.</p>
        </section>
    </main>

    <div class="back-to-home">
        <a href="/" class="back-btn">← Back to Home</a>
    </div>
</div>

<style>
    .terms-container {
        max-width: 800px;
        margin: 0 auto;
        padding: 2rem;
        min-height: 100vh;
        background: linear-gradient(135deg, #1e1e2e 0%, #2a2a3e 100%);
        color: white;
    }

    .terms-header {
        text-align: center;
        margin-bottom: 3rem;
    }

    .terms-header h1 {
        font-size: 3rem;
        margin-bottom: 1rem;
        background: linear-gradient(135deg, #00d4ff 0%, #0099cc 100%);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        background-clip: text;
    }

    .terms-header p {
        font-size: 1rem;
        opacity: 0.7;
        font-style: italic;
    }

    .terms-content {
        display: flex;
        flex-direction: column;
        gap: 2rem;
    }

    .terms-section {
        background: rgba(255, 255, 255, 0.05);
        border-radius: 12px;
        padding: 2rem;
        border: 1px solid rgba(255, 255, 255, 0.1);
        backdrop-filter: blur(10px);
    }

    .terms-section h2 {
        font-size: 1.8rem;
        margin-bottom: 1rem;
        color: #00d4ff;
    }

    .terms-section h3 {
        font-size: 1.3rem;
        margin: 1.5rem 0 0.8rem 0;
        color: #66c2ff;
    }

    .terms-section p {
        line-height: 1.6;
        opacity: 0.9;
        margin-bottom: 1rem;
    }

    .terms-section ul {
        margin-left: 1.5rem;
        margin-bottom: 1rem;
    }

    .terms-section li {
        line-height: 1.6;
        opacity: 0.9;
        margin-bottom: 0.5rem;
    }

    .back-to-home {
        text-align: center;
        margin-top: 3rem;
    }

    .back-btn {
        display: inline-block;
        padding: 0.8rem 1.5rem;
        background: rgba(0, 212, 255, 0.1);
        border: 1px solid #00d4ff;
        border-radius: 8px;
        color: #00d4ff;
        text-decoration: none;
        transition: all 0.3s ease;
    }

    .back-btn:hover {
        background: #00d4ff;
        color: #1e1e2e;
        transform: translateY(-2px);
    }

    @media (max-width: 768px) {
        .terms-container {
            padding: 1rem;
        }

        .terms-header h1 {
            font-size: 2rem;
        }

        .terms-section {
            padding: 1.5rem;
        }
    }
</style>
