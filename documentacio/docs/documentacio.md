---
sidebar_label: 'Documentació projectes'
sidebar_position: 3
---

# Documentació de projectes

La documentació del projecte estarà en una github pages associada al repositori oficial del projecte i es desplegarà automàticament cada vegada que es genere més documentació. 

La documentació d'un projecte pot ser molt diversa. En el nostre cas, imitarem un document intern d'una empresa de desenvolupament. Ha de servir per als nostres desenvolupadors, però també per als directius i els clients finals de l'aplicació. 

La documentació no es fa al final. És una guia per al desenvolupament.

## Apartats de la documentació

0. Promoció 
   - Nom de l'aplicació
   - Descripció en una frase
   - Quí som
   - Video promocional
1. Planificació
   - Necessitat de l'aplicació
      - User Persona (Buscar en Canva plantilles)    
   - Altres solucions existents
   - Principals funcionalitats
   - Guia d'estil https://design.theguardian.com/, https://design.duolingo.com/, https://resources.specialolympics.org/marketing-and-communications/special-olympics-brand
      - Logo
      - Colors
      - Tipografies
      - Icones
      - Layout  (Figma, mockflow...)
2. Desenvolupament
   - Tecnologies emprades
   - Base de dades
   - E/R
   - SQL
   - Proves de programari
   - Estructura del programari
   - UML
   - Casos d'ús
   - Estructura del client
   - Estructura del servidor. (API Documentation)
   - Documentació Scrum (Backlog)
   - Instal·lació de servidors, llibreries...
   - Descripció del procés de desenvolupament
     - Product Roadmap
4. Manual d'usuari
   - Manual d'usuari complet
   - How To Guides
   - Quick Start
   - Troubleshooting Guides
   - FAQs
   - Comunity Docs 
6. Problemes resolts
7. Monetització
8. Propostes de millora
9. Bibliografia
10. Annexos 


## Cóm publicar la documentació

* Cal fer un projecte de web estàtica per a documentació com pot ser `Docusaurus` o `Jupyter Books`. En el nostre cas el farem en https://docusaurus.io/docs 
* Cal crear el Github Pages corresponent. 
* Cal crear el Github Action per publicar automàticament.