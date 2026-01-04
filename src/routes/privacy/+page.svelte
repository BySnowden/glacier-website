<svelte:head>
    <title>Privacy Policy - Glacier Mod Manager</title>
    <meta name="description" content="Privacy policy for Glacier Mod Manager" />
</svelte:head>

<div class="privacy-container">
    <header class="privacy-header">
        <h1>Privacy Policy</h1>
        <p>Last updated: January 4, 2025</p>
    </header>

    <main class="privacy-content">
        <section class="privacy-section">
            <h2>Introduction</h2>
            <p>At Glacier Mod Manager, we take your privacy seriously. This Privacy Policy explains how we collect, use, and protect your information when you use our mod management software.</p>
        </section>

        <section class="privacy-section">
            <h2>Information We Collect</h2>
            <h3>Information You Provide</h3>
            <ul>
                <li>No personal information is required to use Glacier Mod Manager</li>
                <li>We do not collect names, email addresses, or other personal identifiers</li>
            </ul>

            <h3>Automatically Collected Information</h3>
            <ul>
                <li>We may collect anonymous usage statistics to improve the software</li>
                <li>Error logs may be generated locally for debugging purposes</li>
                <li>No personally identifiable information is included in any data collection</li>
            </ul>
        </section>

        <section class="privacy-section">
            <h2>How We Use Information</h2>
            <p>Any information collected is used solely for:</p>
            <ul>
                <li>Improving the functionality and performance of Glacier Mod Manager</li>
                <li>Identifying and fixing bugs or issues</li>
                <li>Understanding how features are used to guide development</li>
            </ul>
        </section>

        <section class="privacy-section">
            <h2>Data Storage and Security</h2>
            <ul>
                <li>All mod management data is stored locally on your device</li>
                <li>We do not maintain servers that store your personal data</li>
                <li>Your mod configurations and preferences remain private and local</li>
                <li>Any data transmission is encrypted and secure</li>
            </ul>
        </section>

        <section class="privacy-section">
            <h2>Third-Party Services</h2>
            <p>Glacier Mod Manager may interact with third-party mod repositories and services. These services have their own privacy policies, which we encourage you to review.</p>
        </section>

        <section class="privacy-section">
            <h2>Open Source</h2>
            <p>Glacier Mod Manager is open-source software. You can review our code, data handling practices, and privacy implementations on our GitHub repository.</p>
        </section>

        <section class="privacy-section">
            <h2>Changes to This Policy</h2>
            <p>We may update this Privacy Policy from time to time. Any changes will be reflected in the "Last updated" date at the top of this policy.</p>
        </section>

        <section class="privacy-section">
            <h2>Contact Us</h2>
            <p>If you have any questions about this Privacy Policy, please contact us through our GitHub repository or community channels.</p>
        </section>
    </main>

    <div class="back-to-home">
        <a href="/" class="back-btn">← Back to Home</a>
    </div>
</div>

<style>
    .privacy-container {
        max-width: 800px;
        margin: 0 auto;
        padding: 2rem;
        min-height: 100vh;
        background: linear-gradient(135deg, #1e1e2e 0%, #2a2a3e 100%);
        color: white;
    }

    .privacy-header {
        text-align: center;
        margin-bottom: 3rem;
    }

    .privacy-header h1 {
        font-size: 3rem;
        margin-bottom: 1rem;
        background: linear-gradient(135deg, #00d4ff 0%, #0099cc 100%);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        background-clip: text;
    }

    .privacy-header p {
        font-size: 1rem;
        opacity: 0.7;
        font-style: italic;
    }

    .privacy-content {
        display: flex;
        flex-direction: column;
        gap: 2rem;
    }

    .privacy-section {
        background: rgba(255, 255, 255, 0.05);
        border-radius: 12px;
        padding: 2rem;
        border: 1px solid rgba(255, 255, 255, 0.1);
        backdrop-filter: blur(10px);
    }

    .privacy-section h2 {
        font-size: 1.8rem;
        margin-bottom: 1rem;
        color: #00d4ff;
    }

    .privacy-section h3 {
        font-size: 1.3rem;
        margin: 1.5rem 0 0.8rem 0;
        color: #66c2ff;
    }

    .privacy-section p {
        line-height: 1.6;
        opacity: 0.9;
        margin-bottom: 1rem;
    }

    .privacy-section ul {
        margin-left: 1.5rem;
        margin-bottom: 1rem;
    }

    .privacy-section li {
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
        .privacy-container {
            padding: 1rem;
        }

        .privacy-header h1 {
            font-size: 2rem;
        }

        .privacy-section {
            padding: 1.5rem;
        }
    }
</style>
