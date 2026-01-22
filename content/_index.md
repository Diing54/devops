---
title: Home
---

<style>
  /* Base Vibes */
  .hero-container {
    padding: 2rem 0;
    font-family: 'JetBrains Mono', 'Fira Code', monospace; /* Authentic dev fonts */
  }

  .terminal-intro {
    background: #1a1b26; /* Arch/Neovim dark theme bg */
    border-left: 4px solid #7aa2f7; /* Accent color */
    padding: 1.5rem;
    border-radius: 0 8px 8px 0;
    margin-bottom: 3rem;
    box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
  }

  .prompt { color: #9ece6a; font-weight: bold; }
  .cursor { animation: blink 1s infinite; }
  
  /* The Tiling Grid (Hyprland Style) */
  .grid-container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 1.5rem;
    margin-top: 2rem;
  }

  /* The Tiles (Notes) */
  .tile {
    background: var(--background-secondary); /* Adapts to Hextra theme */
    border: 1px solid var(--border-color);
    padding: 1.5rem;
    border-radius: 12px;
    transition: all 0.2s ease;
    text-decoration: none !important;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    height: 100%;
  }

  .tile:hover {
    transform: translateY(-4px);
    border-color: #7aa2f7;
    box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
  }

  .tile-header {
    font-size: 1.1rem;
    font-weight: 700;
    margin-bottom: 0.5rem;
    color: var(--text-primary);
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .tile-desc {
    font-size: 0.9rem;
    color: var(--text-secondary);
    line-height: 1.5;
  }

  .tile-meta {
    margin-top: 1rem;
    font-size: 0.75rem;
    color: #565f89;
    font-family: monospace;
    background: rgba(0,0,0,0.05);
    padding: 4px 8px;
    border-radius: 4px;
    width: fit-content;
  }

  /* Icons colors */
  .icon-blue { color: #7aa2f7; }
  .icon-green { color: #9ece6a; }
  .icon-orange { color: #ff9e64; }
  .icon-red { color: #f7768e; }
  .icon-cyan { color: #7dcfff; }

  @keyframes blink { 50% { opacity: 0; } }
</style>

<div class="hero-container">
  <div class="terminal-intro">
    <p style="margin:0; color:#565f89; font-size:0.9rem;">// user: Diing54 | host: arch-legion | status: grinding</p>
    <h1 style="margin-top:0.5rem; font-size:1.8rem;">The DevOps Kernel</h1>
    <p style="margin-top:1rem; font-size:1.1rem; line-height:1.6;">
      <span class="prompt">➜ ~</span> Hello! I'm <strong>Diing</strong>. <br>
      While my blog is the showroom, this is the <strong>Engine Room</strong>. 
      <br><br>
      I am a final-year CS student daily-driving Linux to escape the "it works on my machine" matrix. 
      This is my raw memory buffer—a collection of commands, networking protocols, and system configs I've torn apart and put back together.
      <br><br>
      <span class="prompt">➜ ~</span> echo "No documentation here. Just survival notes."<span class="cursor">_</span>
    </p>
  </div>

  <h3>:: Active Modules</h3>
  
  <div class="grid-container">
    
    <a href="/devops/docs/linux-file-system/" class="tile">
      <div>
        <div class="tile-header">
          <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="icon-orange"><path d="M4 20h16a2 2 0 0 0 2-2V8a2 2 0 0 0-2-2h-7.93a2 2 0 0 1-1.66-.9l-.82-1.2A2 2 0 0 0 7.93 2H4a2 2 0 0 0-2 2v13c0 1.1.9 2 2 2Z"></path></svg>
          Linux Internals
        </div>
        <div class="tile-desc">
          File systems, permissions, and the boot process. The stuff that breaks if you look at it wrong.
        </div>
      </div>
      <div class="tile-meta">/etc /boot /var</div>
    </a>

    <a href="/devops/docs/networking-fundamentals/" class="tile">
      <div>
        <div class="tile-header">
          <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="icon-blue"><circle cx="12" cy="12" r="10"></circle><line x1="2" y1="12" x2="22" y2="12"></line><path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"></path></svg>
          Networking
        </div>
        <div class="tile-desc">
          OSI layers, subnets, and SSH. How packets travel from A to B without getting lost.
        </div>
      </div>
      <div class="tile-meta">ping 127.0.0.1</div>
    </a>

    <a href="/devops/docs/bash-scripting/" class="tile">
      <div>
        <div class="tile-header">
          <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="icon-green"><polyline points="4 17 10 11 4 5"></polyline><line x1="12" y1="19" x2="20" y2="19"></line></svg>
          Shell Scripting
        </div>
        <div class="tile-desc">
          Automating the boring stuff. If I have to type it twice, I script it.
        </div>
      </div>
      <div class="tile-meta">#!/bin/bash</div>
    </a>

    <a href="/devops/docs/" class="tile">
      <div>
        <div class="tile-header">
          <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="icon-red"><path d="m18 16 4-4-4-4"></path><path d="m6 8-4 4 4 4"></path><path d="m14.5 4-5 16"></path></svg>
          Full Index
        </div>
        <div class="tile-desc">
           Raw list of all 7+ notes. The unstructured pile of knowledge.
        </div>
      </div>
      <div class="tile-meta">ls -la</div>
    </a>

  </div>
</div>
