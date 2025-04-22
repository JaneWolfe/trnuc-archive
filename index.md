---
layout: default
---

{% include sidebar.html %}

<!-- Main Content -->
<div class="main">
  <div class="heading-section">
    <h2>TRUTH, RECONCILIATION AND NATIONAL UNITY COMMISSION</h2>
    <h1>FINAL REPORT</h1>
  </div>

  <input type="text" id="searchBar" onkeyup="searchTable()" placeholder="Search by name...">

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
          <td><a href="{{ person.url }}">{{ person.name }}</a></td>
          <td><a href="{{ person.url}}">{{ person.youtube}}</a></td>
          <td><a href="{{ person.pdf }}" target="_blank">PDF</a></td>
          <td><a href="{{ person.url }}">Read their blog</a></td>

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
