---
layout: null
permalink: /index.html
---

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>TRNUC Archive</title>
  <link rel="stylesheet" href="{{ '/style.css' | relative_url }}">
</head>
<body>

{% include loading.html %}

  <!-- Mobile Header -->
<div class="mobile-header">
    <a href="{{ '/' | relative_url }}">
      <img src="https://janewolfe.github.io/trnuc-archive/logo.png" alt="Logo" />
    </a>
    <div class="hamburger-icon" onclick="toggleMobileNav()">
      <span></span>
      <span></span>
      <span></span>
    </div>
  </div>

<p><!-- Sidebar --></p>
<div class="sidebar">
    <a href="{{ '/' | relative_url }}">
      <img src="https://janewolfe.github.io/trnuc-archive/logo.png" alt="TRNUC Logo" />
    </a>
    <h3>THE TRNUC ARCHIVE</h3>
    <nav>
      <a href="#" class="volume">Volume I</a>
      <a href="#" class="section">Introduction</a>
      <a href="#" class="section">Annex I</a>
      <a href="#" class="section">Annex II</a>
      <a href="#" class="section">Annex III</a>
      <a href="#" class="section">Annex IV</a>
      <a href="#" class="volume">Volume II</a>
      <a href="#" class="section">Historical Context</a>
      <a href="#" class="volume">Volume III</a>
      <a href="#" class="section">Legal Framework</a>
      <a href="#" class="volume">Volume IV</a>
      <a href="#" class="section">Amnesty</a>
      <a href="#" class="volume">Volume V</a>
      <a href="#" class="section">Reparations</a>
    </nav>
  </div>

<p><!-- Mobile Nav Menu --></p>
<div id="mobileNav" class="mobile-nav">
    <div class="close" onclick="this.classList.remove('hovered'); toggleMobileNav()" onmouseenter="this.classList.add('hovered')" onmouseleave="this.classList.remove('hovered')">&times;</div>
    <h3>THE TRNUC ARCHIVE</h3>
    <nav>
      <a href="#" class="volume">Volume I</a>
      <a href="#" class="section">Introduction</a>
      <a href="#" class="section">Annex I</a>
      <a href="#" class="section">Annex II</a>
      <a href="#" class="section">Annex III</a>
      <a href="#" class="section">Annex IV</a>
      <a href="#" class="volume">Volume II</a>
      <a href="#" class="section">Historical Context</a>
      <a href="#" class="volume">Volume III</a>
      <a href="#" class="section">Legal Framework</a>
      <a href="#" class="volume">Volume IV</a>
      <a href="#" class="section">Amnesty</a>
      <a href="#" class="volume">Volume V</a>
      <a href="#" class="section">Reparations</a>
    </nav>
  </div>

<script>
    function toggleMobileNav() {
      const nav = document.getElementById('mobileNav');
      const isVisible = nav.classList.contains('show');

      if (isVisible) {
        nav.classList.remove('show');
        nav.addEventListener('transitionend', () => {
          nav.style.display = 'none';
        }, { once: true });
        document.body.style.overflow = 'auto';
      } else {
        nav.style.display = 'block';
        requestAnimationFrame(() => {
          nav.classList.add('show');
        });
        document.body.style.overflow = 'hidden';
      }
    }
</script>

<!-- Main Content -->
<div class="main">
  <div class="heading-section">
    <h2>TRUTH, RECONCILIATION AND NATIONAL UNITY COMMISSION</h2>
    <h1>FINAL REPORT</h1>
  </div>

  <input type="text" id="searchBar" onkeyup="searchTable()" placeholder="Search by name..." />

  <table id="casesTable">
    <thead>
      <tr>
        <th>Case No.</th>
        <th>Name</th>
        <th>Hearing</th>
        <th>Report</th>
        <th>Update</th>
      </tr>
    </thead>
    <tbody>
      {% for person in site.people %}
        <tr>
          <td>{{ person.casenumber }}</td>
          <td><a href="{{ site.baseurl }}{{ person.url }}">{{ person.title }}</a></td>
          <td><a href="{{ site.baseurl }}{{ person.url }}">{{ person.youtube }}</a></td>
          <td><a href="{{ person.pdf | relative_url }}" target="_blank">PDF</a></td>
          <td><a href="{{ site.baseurl }}{{ person.url }}">Read their blog</a></td>
        </tr>
      {% endfor %}
    </tbody>
  </table>
</div>

<!-- Footer -->
<div class="footer">
  Connect with us on our: <strong>Facebook Group</strong> | <strong>Whatsapp Community</strong> | <strong>Youtube Channel</strong>
</div>

<!-- Optional: JavaScript for search -->
<script>
function searchTable() {
  const input = document.getElementById('searchBar').value.toLowerCase();
  const rows = document.querySelectorAll('#casesTable tbody tr');

  rows.forEach(row => {
    const text = row.innerText.toLowerCase();
    row.style.display = text.includes(input) ? '' : 'none';
  });
}
</script>

</body>
</html>
