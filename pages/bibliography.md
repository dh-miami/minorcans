---
title: Bibliography
layout: about
permalink: /bibliography.html
# include CollectionBuilder info at bottom
# credits: true
# Look in _includes/feature for options to easily add features to the page
---
## Bibliography

(Retrieved by [Zotero Collection](https://www.zotero.org/susannalles/collections/CVXCKQA9)) 

<div id="zotero-bib">Loading bibliography...</div>

<script>
  const userID = "1167759";
  const collectionKey = "CVXCKQA9";
  const limit = 100;

  fetch(`https://api.zotero.org/users/${userID}/collections/${collectionKey}/items/top?format=json&limit=${limit}`)
    .then(response => response.json())
    .then(data => {
      const items = data
        .filter(item => item.data.itemType !== "attachment")
        .sort((a, b) => {
          const aLast = a.data.creators?.[0]?.lastName || "";
          const bLast = b.data.creators?.[0]?.lastName || "";
          return aLast.localeCompare(bLast);
        });

      const container = document.getElementById("zotero-bib");
      container.innerHTML = "";

      items.forEach(item => {
        const { title, creators, date, publicationTitle, url } = item.data;
        const authors = creators?.map(c => `${c.lastName}, ${c.firstName}`).join(", ");
        const citation = `${authors}. <i>${title}</i>${publicationTitle ? `. ${publicationTitle}` : ""}, ${date}.`;

        const div = document.createElement("div");
        div.style.marginBottom = "1em";
        div.style.paddingLeft = "2em";
        div.style.textIndent = "-2em";

        div.innerHTML = url
          ? `${citation} <a href="${url}" target="_blank" rel="noopener noreferrer">${url}</a>`
          : citation;

        container.appendChild(div);
      });
    })
    .catch(error => {
      console.error("Error:", error);
      document.getElementById("zotero-bib").innerText = "Failed to load bibliography.";
    });
</script>












