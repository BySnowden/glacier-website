<svelte:head>
    <title>FAQ - Glacier Mod Manager</title>
    <meta name="description" content="Frequently asked questions about Glacier Mod Manager" />
</svelte:head>

<div class="faq-container">
    <header class="faq-header">
        <h1>Frequently Asked Questions</h1>
        <p>Get answers to common questions about Glacier Mod Manager</p>
    </header>

    <main class="faq-content">
        <div class="faq-item">
            <h2>What is Glacier Mod Manager?</h2>
            <p>Glacier is a powerful mod manager designed to simplify the installation, management, and organization of mods for your favorite games. It provides an intuitive interface and automated processes to make modding hassle-free.</p>
        </div>

        <div class="faq-item">
            <h2>Is Glacier free to use?</h2>
            <p>Yes, Glacier Mod Manager is completely free and open-source. You can download and use it without any cost.</p>
        </div>

        <div class="faq-item">
            <h2>Which games does Glacier support?</h2>
            <p>Glacier supports a wide range of popular games. Check our GitHub repository for the most up-to-date list of supported games and planned additions.</p>
        </div>

        <div class="faq-item">
            <h2>How do I install Glacier?</h2>
            <p>Simply download the installer from our homepage and run it. Glacier will guide you through the setup process automatically.</p>
        </div>

        <div class="faq-item">
            <h2>Is my data safe with Glacier?</h2>
            <p>Absolutely. Glacier prioritizes user privacy and security. We don't collect personal data, and all mod management happens locally on your machine.</p>
        </div>

        <div class="faq-item">
            <h2>Can I contribute to Glacier's development?</h2>
            <p>Yes! Glacier is open-source and we welcome contributions. Visit our GitHub repository to learn how you can help improve Glacier.</p>
        </div>

        <div class="faq-item">
            <h2>Where can I get help if I have issues?</h2>
            <p>You can open an issue on our GitHub repository, check our documentation, or reach out to the community through our social media channels.</p>
        </div>
    </main>

    <div class="back-to-home">
        <a href="/" class="back-btn">← Back to Home</a>
    </div>
</div>

<style>
    .faq-container {
        max-width: 800px;
        margin: 0 auto;
        padding: 2rem;
        min-height: 100vh;
        background: linear-gradient(135deg, #1e1e2e 0%, #2a2a3e 100%);
        color: white;
    }

    .faq-header {
        text-align: center;
        margin-bottom: 3rem;
    }

    .faq-header h1 {
        font-size: 3rem;
        margin-bottom: 1rem;
        background: linear-gradient(135deg, #00d4ff 0%, #0099cc 100%);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        background-clip: text;
    }

    .faq-header p {
        font-size: 1.2rem;
        opacity: 0.8;
    }

    .faq-content {
        display: flex;
        flex-direction: column;
        gap: 2rem;
    }

    .faq-item {
        background: rgba(255, 255, 255, 0.05);
        border-radius: 12px;
        padding: 2rem;
        border: 1px solid rgba(255, 255, 255, 0.1);
        backdrop-filter: blur(10px);
        transition: all 0.3s ease;
    }

    .faq-item:hover {
        transform: translateY(-2px);
        border-color: rgba(0, 212, 255, 0.3);
        box-shadow: 0 8px 32px rgba(0, 212, 255, 0.1);
    }

    .faq-item h2 {
        font-size: 1.5rem;
        margin-bottom: 1rem;
        color: #00d4ff;
    }

    .faq-item p {
        line-height: 1.6;
        opacity: 0.9;
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
        .faq-container {
            padding: 1rem;
        }

        .faq-header h1 {
            font-size: 2rem;
        }

        .faq-item {
            padding: 1.5rem;
        }
    }
</style>
