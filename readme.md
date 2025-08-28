# 🧠 Dialexis - Générateur de dissertations philosophiques assisté par vecteurs

## 📖 Description simple

Dialexis est un projet qui vise à **générer automatiquement des dissertations philosophiques** à partir d’une citation donnée.  
L’idée est de combiner :
- des **embeddings sémantiques** pour analyser des œuvres de référence,
- des **algorithmes vectoriels** pour structurer des arguments (thèse / antithèse / synthèse),
- un **LLM** (via [Ollama](https://ollama.ai/)) pour formuler les arguments et broder le texte.

Le résultat final suit la structure classique d’une dissertation :
- **Introduction** (analyse citation + problématique),
- **Développement** (thèse, antithèse, synthèse),
- **Conclusion** (bilan + ouverture).

---

## ⚙️ Description technique

### 1. Prétraitement
- Extraction du texte `<p>` dans des livres de référence (format HTML).
- Découpage en phrases → chaque phrase est une unité de sens.

### 2. Vectorisation
- Embedding de chaque phrase via **Ollama Embeddings** (LangChain).
- Calcul de proximités sémantiques (cosine similarity).
- Sélection de **triplets de phrases proches** → matière brute.

### 3. Génération d’arguments
- Envoi des triplets à Ollama (LLM).
- Génération d’arguments formulés.  
- Vectorisation des arguments.

### 4. Construction dialectique
- Sélection des arguments proches → **Thèse**.
- Recherche des vecteurs opposés → **Antithèse**.
- Calcul d’un vecteur normal au plan thèse/antithèse → **Synthèse**.

### 5. Assemblage final
- **Introduction** : analyse citation + problématique.  
- **Développement** : thèse → antithèse → synthèse.  
- **Conclusion** : reformulation problématique + bilan + ouverture (exploration d’une direction vectorielle non utilisée).

---

## ✅ Check-list

### Étapes conceptuelles
- [x] Définir le pipeline global (intro / développement / conclusion).  
- [x] Identifier les sources (livres de référence en HTML).  
- [x] Choisir Ollama + LangChain comme stack.  
- [ ] Tester la cohérence des embeddings sur les citations.  
- [ ] Expérimenter la sélection de triplets par similarité.  
- [ ] Valider la construction thèse/antithèse/synthèse par vecteurs.  
- [ ] Intégrer la broderie finale (intro + conclusion).  

### Étapes techniques
- [ ] Extraction du texte HTML en phrases.  
- [ ] Génération des embeddings avec Ollama.  
- [ ] Recherche brute force de triplets proches.  
- [ ] Prompting LLM pour formuler des arguments.  
- [ ] Vectorisation des arguments.  
- [ ] Calcul dialectique (opposés + vecteur normal).  
- [ ] Génération du texte complet via Ollama.  

---

## 📂 Structure du projet

Voici l’organisation des fichiers pour ce projet :

```
├─ data/
│   ├─ la-connaissance-de-la-vie-de-georges-canguilhem.html
│   ├─ le-mur-invisible-de-marlen-haushofer.html
│   ├─ vingt-mille-lieues-sous-les-mers-de-jules-verne.html
│   └─ raw.zip
├─ .gitignore
├─ dialexis_dev.ipynb
├─ main.py
└─ readme.md
```

> ⚠️ Les fichiers HTML **ne sont pas fournis** pour respecter les droits d’auteur.
> L’utilisateur doit fournir lui-même ses fichiers HTML.

À titre indicatif, vous pouvez par exemple convertir en HTML vos propres documents ou explorer des publications disponibles en ligne, comme certains articles sur :  
👉 [https://potethiquealentstics.over-blog.com/tag/cpge/](https://potethiquealentstics.over-blog.com/tag/cpge/)  (Ne pouvant pas etre publié ici a cause de l'article 10 des CGU)

---

## ⚠️ Avertissement et déresponsabilisation

Ce projet est un outil expérimental destiné à l’exploration des **modèles de langage, embeddings et méthodes de génération de texte**.  
Il est fourni **sans garantie d’exactitude, de pertinence ou d’adéquation** à un usage particulier.

- ❌ Il est **strictement interdit** d’utiliser cet outil pour la **triche académique**, notamment lors d’examens, concours, ou évaluations scolaires/universitaires.  
- ✅ L’usage recommandé est la **recherche personnelle, l’expérimentation technique, la créativité et l’apprentissage**.  

L’auteur décline toute responsabilité en cas d’utilisation abusive, frauduleuse ou non conforme à cet esprit.

---

## 📜 Licence

Ce projet est distribué sous licence **MIT**.  
Voir le fichier [LICENSE](LICENSE) pour plus de détails.
