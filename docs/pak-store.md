---
hide:
  - navigation
  - toc
---

# NextUI Community Paks

NextUI allows you to add functionality to the system in the form of Paks.

The NextUI Community has created these amazing paks which are available to download right on your device through the Pak Store.

Simply connect to Wi-Fi, select Pak Store from the tools menu and try out these paks.

Interested in making a pak? Community member Jose Diaz-Gonzalez has put together a [fantastic guide](https://josediazgonzalez.com/2025/06/16/writing-a-pak-for-the-minui-and-nextui-launchers/).

<style>
.pak-store-container {
    --ps-bg: var(--md-default-bg-color);
    --ps-bg-card: var(--md-code-bg-color);
    --ps-text: var(--md-typeset-color);
    --ps-text-muted: var(--md-default-fg-color--lighter);
    --ps-accent: #9B2256;
    --ps-border: var(--md-default-fg-color--lightest);
    --ps-success: #4ecca3;
    --ps-warning: #ffc93c;
}

.pak-store-container * {
    box-sizing: border-box;
}

.pak-filters {
    display: flex;
    flex-wrap: wrap;
    gap: 12px;
    margin-bottom: 24px;
    padding-bottom: 16px;
    border-bottom: 1px solid var(--ps-border);
}

.pak-filter-group {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    align-items: center;
}

.pak-filter-label {
    color: var(--ps-text-muted);
    font-size: 0.8rem;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.5px;
}

.pak-filter-btn {
    padding: 6px 12px;
    font-size: 0.8rem;
    background: var(--ps-bg-card);
    border: 1px solid var(--ps-border);
    border-radius: 6px;
    color: var(--ps-text-muted);
    cursor: pointer;
    transition: all 0.2s;
    font-family: inherit;
}

.pak-filter-btn:hover {
    border-color: var(--ps-accent);
    color: var(--ps-text);
}

.pak-filter-btn.active {
    background: var(--ps-accent);
    border-color: var(--ps-accent);
    color: white;
}

.pak-search {
    flex: 1;
    min-width: 200px;
    max-width: 400px;
}

.pak-search-input {
    width: 100%;
    padding: 8px 12px;
    font-size: 0.9rem;
    background: var(--ps-bg-card);
    border: 1px solid var(--ps-border);
    border-radius: 6px;
    color: var(--ps-text);
    outline: none;
    font-family: inherit;
}

.pak-search-input:focus {
    border-color: var(--ps-accent);
}

.pak-search-input::placeholder {
    color: var(--ps-text-muted);
}

.pak-stats {
    display: flex;
    gap: 16px;
    color: var(--ps-text-muted);
    font-size: 0.85rem;
    margin-bottom: 16px;
}

.pak-stat-value {
    color: var(--ps-accent);
    font-weight: 600;
}

.paks-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(380px, 1fr));
    gap: 16px;
    margin-bottom: 32px;
}

.pak-card {
    background: var(--ps-bg-card);
    border: 1px solid var(--ps-border);
    border-radius: 10px;
    padding: 16px;
    display: flex;
    flex-direction: column;
    transition: border-color 0.2s;
}

.pak-card:hover {
    border-color: var(--ps-accent);
}

.pak-header {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    margin-bottom: 10px;
    gap: 10px;
}

.pak-header-badges {
    display: flex;
    align-items: center;
    gap: 6px;
    flex-shrink: 0;
}

.pak-title {
    display: flex;
    flex-direction: column;
    gap: 2px;
}

.pak-name {
    font-size: 1rem;
    font-weight: 600;
    color: var(--ps-text);
    margin: 0;
}

.pak-type {
    padding: 3px 8px;
    font-size: 0.7rem;
    font-weight: 600;
    border-radius: 4px;
    text-transform: uppercase;
    display: inline-flex;
    align-items: center;
}

.pak-type.tool {
    background: rgba(155, 34, 86, 0.15);
    color: var(--ps-accent);
}

.pak-type.emu {
    background: rgba(155, 34, 86, 0.15);
    color: var(--ps-accent);
}

.pak-badges {
    display: flex;
    gap: 6px;
    margin-bottom: 10px;
}

.pak-badge {
    padding: 3px 8px;
    font-size: 0.7rem;
    border-radius: 4px;
    font-weight: 600;
    text-transform: uppercase;
    display: inline-flex;
    align-items: center;
}

.pak-badge.official {
    background: rgba(78, 204, 163, 0.2);
    color: var(--ps-success);
}

.pak-badge.large {
    background: rgba(255, 201, 60, 0.2);
    color: var(--ps-warning);
}

.pak-description {
    color: var(--ps-text-muted);
    font-size: 0.85rem;
    margin-bottom: 12px;
    line-height: 1.5;
}

.pak-meta {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
    margin-bottom: 10px;
}

.pak-version {
    font-size: 0.75rem;
    color: var(--ps-text-muted);
}

.pak-author {
    font-size: 0.75rem;
    color: var(--ps-text-muted);
}

.pak-categories {
    display: flex;
    flex-wrap: wrap;
    gap: 4px;
    margin-bottom: 10px;
}

.pak-category {
    padding: 2px 6px;
    font-size: 0.65rem;
    background: var(--ps-bg);
    border-radius: 4px;
    color: var(--ps-text-muted);
}

.pak-platforms {
    display: flex;
    flex-wrap: wrap;
    gap: 4px;
    margin-bottom: 12px;
}

.pak-platform {
    padding: 2px 5px;
    font-size: 0.6rem;
    background: rgba(255, 201, 60, 0.15);
    border-radius: 3px;
    color: var(--ps-warning);
    text-transform: uppercase;
    font-weight: 500;
}

.pak-link {
    display: block;
    width: 100%;
    padding: 8px 12px;
    font-size: 0.8rem;
    text-align: center;
    text-decoration: none !important;
    border-radius: 6px;
    background: var(--ps-accent);
    color: white !important;
    font-weight: 600;
    margin-top: auto;
    transition: opacity 0.2s;
}

.pak-link:hover {
    opacity: 0.9;
}

.pak-no-results {
    text-align: center;
    padding: 40px 20px;
    color: var(--ps-text-muted);
}

.pak-loading {
    text-align: center;
    padding: 40px 20px;
    color: var(--ps-text-muted);
}

@media (max-width: 600px) {
    .pak-filters {
        flex-direction: column;
    }

    .pak-search {
        max-width: none;
    }

    .pak-filter-group {
        width: 100%;
    }

    .paks-grid {
        grid-template-columns: 1fr;
    }
}
</style>

<div class="pak-store-container">
    <div class="pak-filters">
        <div class="pak-filter-group">
            <span class="pak-filter-label">Type:</span>
            <button class="pak-filter-btn active" data-filter="type" data-value="all">All</button>
            <button class="pak-filter-btn" data-filter="type" data-value="TOOL">Tools</button>
            <button class="pak-filter-btn" data-filter="type" data-value="EMU">Emulators</button>
        </div>
        <div class="pak-search">
            <input type="text" class="pak-search-input" id="pak-search" placeholder="Search paks...">
        </div>
    </div>
    <div class="pak-filters" id="pak-category-filters">
        <div class="pak-filter-group">
            <span class="pak-filter-label">Category:</span>
            <button class="pak-filter-btn active" data-filter="category" data-value="all">All</button>
        </div>
    </div>
    <div class="pak-filters" id="pak-platform-filters">
        <div class="pak-filter-group">
            <span class="pak-filter-label">Platform:</span>
            <button class="pak-filter-btn active" data-filter="platform" data-value="all">All</button>
        </div>
    </div>
    <div class="pak-stats">
        <span>Total: <span class="pak-stat-value" id="pak-total">-</span></span>
        <span>Showing: <span class="pak-stat-value" id="pak-showing">-</span></span>
    </div>
    <div id="paks-grid-container">
        <div class="pak-loading">Loading paks...</div>
    </div>
</div>

<script>
(function() {
    const STOREFRONT_URL = 'https://raw.githubusercontent.com/LoveRetro/nextui-pak-store/refs/heads/gh-pages/storefront.json';
    const OFFICIAL_PAKS = ['Pak Store', 'Over The Air Updater'];
    const SUPPORTED_PLATFORMS = ['tg5040', 'tg5050'];

    let allPaks = [];
    let currentFilters = { type: 'all', category: 'all', platform: 'all', search: '' };

    function isOfficial(pak) {
        return OFFICIAL_PAKS.includes(pak.storefront_name || pak.name || '');
    }

    function sortPaks(paks) {
        return [...paks].sort((a, b) => {
            const nameA = a.storefront_name || a.name || '';
            const nameB = b.storefront_name || b.name || '';
            if (nameA === 'Pak Store') return -1;
            if (nameB === 'Pak Store') return 1;
            if (nameA === 'Over The Air Updater') return -1;
            if (nameB === 'Over The Air Updater') return 1;
            return nameA.localeCompare(nameB);
        });
    }

    function hasSupportedPlatform(pak) {
        if (!pak.platforms || !pak.platforms.length) return false;
        return pak.platforms.some(p => SUPPORTED_PLATFORMS.includes(p.toLowerCase()));
    }

    function getSupportedPlatforms(pak) {
        if (!pak.platforms) return [];
        return pak.platforms.filter(p => SUPPORTED_PLATFORMS.includes(p.toLowerCase()));
    }

    function filterPaks(paks) {
        const filtered = paks.filter(pak => {
            if (pak.disabled || !pak.name || !pak.version) return false;
            if (!hasSupportedPlatform(pak)) return false;
            if (currentFilters.type !== 'all' && pak.type !== currentFilters.type) return false;
            if (currentFilters.category !== 'all' && (!pak.categories || !pak.categories.includes(currentFilters.category))) return false;
            if (currentFilters.platform !== 'all' && (!pak.platforms || !pak.platforms.some(p => p.toLowerCase() === currentFilters.platform.toLowerCase()))) return false;
            if (currentFilters.search) {
                const s = currentFilters.search.toLowerCase();
                const nameMatch = (pak.storefront_name || pak.name || '').toLowerCase().includes(s);
                const descMatch = (pak.description || '').toLowerCase().includes(s);
                const authorMatch = (pak.author || '').toLowerCase().includes(s);
                if (!nameMatch && !descMatch && !authorMatch) return false;
            }
            return true;
        });
        return sortPaks(filtered);
    }

    function escapeHtml(text) {
        if (!text) return '';
        const div = document.createElement('div');
        div.textContent = text;
        return div.innerHTML;
    }

    function createPakCard(pak) {
        const name = pak.storefront_name || pak.name || 'Unknown';
        const categories = pak.categories || [];
        const platforms = getSupportedPlatforms(pak);
        const official = isOfficial(pak);

        return `
            <div class="pak-card">
                <div class="pak-header">
                    <div class="pak-title">
                        <span class="pak-name">${escapeHtml(name)}</span>
                        ${pak.author ? `<span class="pak-author">by ${escapeHtml(pak.author)}</span>` : ''}
                    </div>
                    <div class="pak-header-badges">
                        ${official ? '<span class="pak-badge official">Official</span>' : ''}
                        <span class="pak-type ${pak.type.toLowerCase()}">${pak.type === 'EMU' ? 'Emulator' : pak.type}</span>
                    </div>
                </div>
                ${pak.large_pak ? '<div class="pak-badges"><span class="pak-badge large">Large</span></div>' : ''}
                <p class="pak-description">${escapeHtml(pak.description || 'No description available.')}</p>
                ${categories.length ? `<div class="pak-categories">${categories.map(c => `<span class="pak-category">${escapeHtml(c)}</span>`).join('')}</div>` : ''}
                ${platforms.length ? `<div class="pak-platforms">${platforms.map(p => `<span class="pak-platform">${escapeHtml(p)}</span>`).join('')}</div>` : ''}
                <a href="${escapeHtml(pak.repo_url)}" target="_blank" class="pak-link">View on GitHub</a>
            </div>
        `;
    }

    function renderPaks(paks) {
        const container = document.getElementById('paks-grid-container');
        const filtered = filterPaks(paks);
        document.getElementById('pak-showing').textContent = filtered.length;

        if (!filtered.length) {
            container.innerHTML = '<div class="pak-no-results"><strong>No paks found</strong><br>Try adjusting your filters or search.</div>';
            return;
        }
        container.innerHTML = `<div class="paks-grid">${filtered.map(createPakCard).join('')}</div>`;
    }

    function getCategories(paks) {
        const cats = new Set();
        paks.forEach(p => (p.categories || []).forEach(c => cats.add(c)));
        return Array.from(cats).sort();
    }

    function setupFilters() {
        document.addEventListener('click', e => {
            if (e.target.classList.contains('pak-filter-btn')) {
                const btn = e.target;
                const type = btn.dataset.filter;
                document.querySelectorAll(`[data-filter="${type}"]`).forEach(b => b.classList.remove('active'));
                btn.classList.add('active');
                currentFilters[type] = btn.dataset.value;
                renderPaks(allPaks);
            }
        });
        document.getElementById('pak-search').addEventListener('input', e => {
            currentFilters.search = e.target.value;
            renderPaks(allPaks);
        });
    }

    async function init() {
        try {
            const res = await fetch(STOREFRONT_URL);
            const data = await res.json();
            allPaks = data.paks || [];
        } catch (e) {
            document.getElementById('paks-grid-container').innerHTML = '<div class="pak-no-results">Failed to load paks.</div>';
            return;
        }

        const enabled = allPaks.filter(p => !p.disabled && p.name && p.version && hasSupportedPlatform(p));
        document.getElementById('pak-total').textContent = enabled.length;

        const cats = getCategories(enabled);
        const catContainer = document.querySelector('#pak-category-filters .pak-filter-group');
        cats.forEach(cat => {
            const btn = document.createElement('button');
            btn.className = 'pak-filter-btn';
            btn.dataset.filter = 'category';
            btn.dataset.value = cat;
            btn.textContent = cat;
            catContainer.appendChild(btn);
        });

        const platformContainer = document.querySelector('#pak-platform-filters .pak-filter-group');
        SUPPORTED_PLATFORMS.forEach(platform => {
            const btn = document.createElement('button');
            btn.className = 'pak-filter-btn';
            btn.dataset.filter = 'platform';
            btn.dataset.value = platform;
            btn.textContent = platform.toUpperCase();
            platformContainer.appendChild(btn);
        });

        setupFilters();
        renderPaks(allPaks);
    }

    init();
})();
</script>
