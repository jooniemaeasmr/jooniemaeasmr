// Posts database - add all your posts here
const postsDatabase = [
    {
        title: "The Art of Paper Sounds for Deep Sleep",
        description: "Discover the soothing world of paper ASMR. From gentle page turning to crisp paper folding, these delicate sounds create the perfect atmosphere for relaxation and sleep.",
        url: "posts/paper-sounds-sleep.html",
        date: "2024-12-01",
        category: "Paper ASMR",
        tags: ["paper", "sleep", "relaxation", "page turning"]
    },
    {
        title: "Writing ASMR: Pen on Paper Meditation",
        description: "The rhythmic scratch of pen on paper has a uniquely calming quality. Explore how different writing instruments and paper textures combine to create deeply relaxing soundscapes.",
        url: "posts/writing-asmr-meditation.html",
        date: "2024-11-28",
        category: "Writing ASMR",
        tags: ["writing", "pen", "paper", "meditation"]
    },
    {
        title: "Crinkly Textures: Nature's Relaxation Sound",
        description: "Crinkly sounds tap into something primal and comforting. Whether it's tissue paper, plastic wrap, or natural materials, these textures create unpredictable yet soothing patterns.",
        url: "posts/crinkly-textures-relaxation.html",
        date: "2024-11-25",
        category: "Crinkly ASMR",
        tags: ["crinkly", "texture", "relaxation", "nature"]
    }
    // Add more posts as you create them
];

function searchPosts() {
    const searchInput = document.getElementById('searchInput');
    const searchResults = document.getElementById('searchResults');
    const query = searchInput.value.toLowerCase().trim();
    
    if (query.length < 2) {
        searchResults.innerHTML = '';
        searchResults.style.display = 'none';
        return;
    }
    
    const results = postsDatabase.filter(post => {
        return post.title.toLowerCase().includes(query) ||
               post.description.toLowerCase().includes(query) ||
               post.category.toLowerCase().includes(query) ||
               post.tags.some(tag => tag.toLowerCase().includes(query));
    });
    
    if (results.length === 0) {
        searchResults.innerHTML = '<div class="search-result">No posts found</div>';
        searchResults.style.display = 'block';
        return;
    }
    
    let resultsHTML = '';
    results.forEach(post => {
        resultsHTML += `
            <div class="search-result">
                <h3><a href="${post.url}">${post.title}</a></h3>
                <p class="search-meta">${post.date} • ${post.category}</p>
                <p>${post.description.substring(0, 150)}...</p>
            </div>
        `;
    });
    
    searchResults.innerHTML = resultsHTML;
    searchResults.style.display = 'block';
}

// Search on Enter key
document.addEventListener('DOMContentLoaded', function() {
    const searchInput = document.getElementById('searchInput');
    if (searchInput) {
        searchInput.addEventListener('keyup', function(event) {
            if (event.key === 'Enter') {
                searchPosts();
            }
        });
        
        // Also search as user types (debounced)
        let searchTimeout;
        searchInput.addEventListener('input', function() {
            clearTimeout(searchTimeout);
            searchTimeout = setTimeout(searchPosts, 300);
        });
    }
});

// Close search results when clicking outside
document.addEventListener('click', function(event) {
    const searchContainer = document.querySelector('.search-container');
    const searchResults = document.getElementById('searchResults');
    
    if (searchContainer && !searchContainer.contains(event.target)) {
        searchResults.style.display = 'none';
    }
});