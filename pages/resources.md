---
title: Resources
layout: about
permalink: /resources.html
# include CollectionBuilder info at bottom
credits: false
# Edit the markdown on in this file to describe your collection
# Look in _includes/feature for options to easily add features to the page
---

## Resources 

- Saint Augustine Historical Society, <https://staughs.com/> (Search by [Keyword](https://staughs.catalogaccess.com/search) or [Advanced Search](https://staughs.catalogaccess.com/advanced-search))
    * [Minorcan Resources](https://staughs.com/wp-content/uploads/2024/01/Minorcan-Resources.pdf) 
- The Minorcan Studies Project, <https://minorcanstudiesproject.omeka.net/>
- The Turnbull Settlement “Smyrnea", New Smyrna Museum of History (2016), <https://nsbhistory.org/the-turnbull-settlement-smyrnea/#aboutsmyrnea>. 
- The Missing Minorcans. Discovering their Story and Finding their Graves, <https://minorcans.com/>
- La Florida. The Interactive Digital Archive of the Americas, <https://laflorida.org/>. 
- Florida Collection, Slave Societies Digital Archive, <https://www.slavesocieties.org/collections?name=Florida>
    * [Archivo de la Diócesis de St. Augustine, Libro Baptismos de gente de color, 1793-1807](https://www.slavesocieties.org/assets/documents/Collections/Florida/St_Augustine_Bautismos_1793_1807_Transcription.pdf) (Transcription by Elvira Aballí Morell, Vanderbilt University)
    * [Baptisms, Burials and Marriages - 16th & 17th Centuries](https://www.slavesocieties.org/assets/documents/Collections/Florida/St_Augustine_1594_1644_Transcription.pdf) (Transcription by Saber Grey, University of South Florida)
    * [Baptisms - 1720-1737](https://www.slavesocieties.org/assets/documents/Collections/Florida/St_Augustine_1720_1737_Transcription.pdf) (Transcription by Erin Stone, Vanderbilt University)
    * [White Marriages - 1784-1802](https://www.slavesocieties.org/assets/documents/Collections/Florida/St_Augustine_White_Marriages_1784_1801_Transcription.pdf) (Transcription by Elvira Aballí Morell, Vanderbilt University)
- Florida History Online, University of North Florida, <https://history.domains.unf.edu/floridahistoryonline/>


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












