---
marp: true
theme: default
paginate: true
style: |
  section {
    font-family: 'Inter', 'SF Pro Display', 'Segoe UI', sans-serif;
    background: linear-gradient(135deg, #0f0f1a 0%, #1a1a2e 50%, #16213e 100%);
    color: #e8e8e8;
    position: relative;
  }
  section > * {
    position: relative;
    z-index: 1;
  }
  section[data-marpit-pagination]::after {
    z-index: 2;
  }
  h1 {
    color: #00d4aa;
    font-weight: 700;
    text-shadow: 0 0 30px rgba(0, 212, 170, 0.3);
  }
  h2 {
    color: #64b5f6;
    font-weight: 600;
  }
  strong {
    color: #00d4aa;
  }
  a {
    color: #64b5f6;
  }
  code {
    background-color: rgba(255, 255, 255, 0.1);
    border-radius: 4px;
    padding: 2px 6px;
    color: #ffc66d;
  }
  li {
    margin-bottom: 0.3em;
  }
  /* Darcula theme (PhpStorm) */
  pre {
    background-color: #2b2b2b;
    border-radius: 8px;
    color: #a9b7c6;
  }
  pre code {
    background-color: transparent;
    color: #a9b7c6;
  }
  pre code .hljs-keyword {
    color: #cc7832;
  }
  pre code .hljs-type,
  pre code .hljs-built_in {
    color: #ffc66d;
  }
  pre code .hljs-string {
    color: #6a8759;
  }
  pre code .hljs-comment {
    color: #629755;
    font-style: italic;
  }
  pre code .hljs-comment .hljs-doctag {
    color: #629755 !important;
    font-style: italic;
    font-weight: bold;
  }
  pre code .hljs-phpdoc {
    color: #629755 !important;
    font-style: italic;
  }
  pre code .hljs-function,
  pre code .hljs-title {
    color: #ffc66d;
  }
  pre code .hljs-variable,
  pre code .hljs-params {
    color: #a9b7c6;
  }
  pre code .hljs-number {
    color: #6897bb;
  }
  pre code .hljs-class,
  pre code .hljs-title.class_ {
    color: #a9b7c6;
  }
  pre code .hljs-attr,
  pre code .hljs-property {
    color: #9876aa;
  }
  pre code .hljs-doctag {
    color: #629755;
    font-style: italic;
  }
  pre code .hljs-meta {
    color: #bbb529;
  }
  .columns {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1rem;
  }
  .highlight {
    background: linear-gradient(120deg, #00d4aa 0%, #64b5f6 100%);
    padding: 0.2em 0.4em;
    border-radius: 4px;
    color: #0f0f1a;
  }
  section::after {
    color: rgba(255, 255, 255, 0.5);
  }
  .stat-box {
    background: rgba(255, 255, 255, 0.05);
    border-left: 4px solid #00d4aa;
    padding: 1rem;
    margin: 0.5rem 0;
  }
  table {
    background: transparent !important;
    border-collapse: collapse !important;
    width: auto !important;
  }
  th, td {
    background: rgba(43, 43, 43, 0.95) !important;
    color: #e8e8e8 !important;
    padding: 0.5rem 1rem !important;
    border: 1px solid #00d4aa !important;
  }
  th {
    background: #16213e !important;
    color: #ffffff !important;
    font-weight: 600 !important;
  }
  tr:nth-child(even) td {
    background: rgba(60, 60, 60, 0.95) !important;
  }
---

