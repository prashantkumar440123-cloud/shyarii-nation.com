<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SoulWords | 50+ English Shayari</title>
    <style>
        :root {
            --bg: #fdfcfb;
            --accent: #6c5ce7;
            --text: #2d3436;
        }
        body { font-family: 'Georgia', serif; background: var(--bg); margin: 0; color: var(--text); }
        
        header { background: white; padding: 40px 20px; text-align: center; border-bottom: 1px solid #eee; }
        h1 { margin: 0; font-style: italic; letter-spacing: 2px; color: var(--accent); }

        .search-container { margin: 20px auto; max-width: 500px; padding: 0 20px; }
        #searchBox { width: 100%; padding: 12px; border-radius: 30px; border: 1px solid #ddd; outline: none; text-align: center; font-size: 1rem; }

        .container { max-width: 900px; margin: auto; padding: 20px; display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); gap: 25px; }

        /* Shayari Card Style */
        .shayari-card { 
            background: white; padding: 30px; border-radius: 15px; 
            box-shadow: 0 10px 20px rgba(0,0,0,0.05); border-left: 5px solid var(--accent);
            transition: 0.3s; position: relative;
        }
        .shayari-card:hover { transform: translateY(-5px); box-shadow: 0 15px 30px rgba(0,0,0,0.1); }
        .text { font-size: 1.2rem; line-height: 1.6; margin-bottom: 20px; color: #444; }
        .tag { font-size: 0.8rem; font-family: sans-serif; color: #999; text-transform: uppercase; letter-spacing: 1px; }

        .copy-btn { 
            background: var(--accent); color: white; border: none; padding: 8px 15px; 
            border-radius: 5px; cursor: pointer; float: right; font-family: sans-serif; font-size: 0.8rem;
        }
        .copy-btn:active { opacity: 0.7; }

        #toast { visibility: hidden; position: fixed; bottom: 20px; left: 50%; transform: translateX(-50%); background: #333; color: white; padding: 10px 20px; border-radius: 5px; }
        #toast.show { visibility: visible; }
    </style>
</head>
<body>

<header>
    <h1>SoulWords</h1>
    <p>Elegant English Shayari & Quotes</p>
    <div class="search-container">
        <input type="text" id="searchBox" placeholder="Search by keyword (Love, Life, Sad...)" onkeyup="searchShayari()">
    </div>
</header>

<div class="container" id="shayariGrid">
    </div>

<div id="toast">Copied to Clipboard! ✨</div>

<script>
    const shayaris = [
        { t: "The stars don't shine without darkness.", c: "Life" },
        { t: "In the garden of my soul, you are the only rose.", c: "Love" },
        { t: "Heavy hearts like heavy clouds, best relieved by letting a little water go.", c: "Sad" },
        { t: "I found my home between the pages of your heart.", c: "Love" },
        { t: "Life is short, but the memories we make are eternal.", c: "Life" },
        { t: "Silence is the loudest scream of a broken heart.", c: "Sad" },
        { t: "Be the sunshine in someone's cloudy day.", c: "Life" },
        { t: "My love for you is a journey, starting at forever and ending at never.", c: "Love" },
        { t: "Sometimes you have to let go to see if there was anything worth holding on to.", c: "Sad" },
        { t: "Dream as if you'll live forever, live as if you'll die today.", c: "Life" },
        // ... (Repeat or Add more to reach 50)
    ];

    // Array ko 50 tak bharne ke liye (Demos)
    for(let i=11; i<=50; i++) {
        shayaris.push({ t: "Quote Number " + i + ": Collect moments, not things. Life is a beautiful journey.", c: i % 2 == 0 ? "Life" : "Love" });
    }

    const grid = document.getElementById('shayariGrid');

    function displayShayaris(list) {
        grid.innerHTML = '';
        list.forEach(s => {
            const card = document.createElement('div');
            card.className = 'shayari-card';
            card.innerHTML = `
                <div class="text">"${s.t}"</div>
                <span class="tag">#${s.c}</span>
                <button class="copy-btn" onclick="copyText('${s.t.replace(/'/g, "\\'")}')">COPY</button>
            `;
            grid.appendChild(card);
        });
    }

    function copyText(val) {
        navigator.clipboard.writeText(val);
        const t = document.getElementById('toast');
        t.className = 'show';
        setTimeout(() => t.className = '', 2000);
    }

    function searchShayari() {
        const term = document.getElementById('searchBox').value.toLowerCase();
        const filtered = shayaris.filter(s => s.t.toLowerCase().includes(term) || s.c.toLowerCase().includes(term));
        displayShayaris(filtered);
    }

    displayShayaris(shayaris);
</script>

</body>
</html>
