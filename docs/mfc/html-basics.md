---
title: Éléments fondamentaux relatifs à HTML
ms.date: 11/04/2016
helpviewer_keywords:
- HTML [MFC], about HTML
ms.assetid: aab8ea9f-12d4-4bdd-a585-ac3124081a2a
ms.openlocfilehash: 63a866786abc3b1eaa87a06492b43b1c9e354882
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62262994"
---
# <a name="html-basics"></a>Éléments fondamentaux relatifs à HTML

La plupart des navigateurs ont la capacité d'examiner la source HTML des pages que vous consultez. Lorsque vous affichez la source, vous verrez un nombre HTML (Hypertext markup) de balises de langue, entouré de crochets pointus (<>), entrecoupées avec du texte.

Les étapes ci-dessous utilisent les balises HTML pour générer une page Web. Dans ces étapes, vous saisirez le texte en clair dans un fichier grâce au Bloc-notes, vous apporterez des modifications, enregistrerez le fichier, puis rechargerez la page du navigateur pour afficher vos modifications.

#### <a name="to-create-an-html-file"></a>Pour créer un fichier HTML

1. Ouvrez le Bloc-notes ou un éditeur de texte brut.

1. À partir de la **fichier** menu, choisissez **New**.

1. Tapez les lignes suivantes :

```
<HTML>
<HEAD>
<TITLE>Top HTML Tags</TITLE>
</HEAD>
</HTML>
```

1. À partir de la **fichier** menu, choisissez **enregistrer**, enregistrez le fichier sous c:\webpages\First.htm. Laissez le fichier ouvert dans l'éditeur.

1. Commutateur vers votre navigateur et depuis le **fichier** menu, choisissez **Open**, ou type *file://C:/webpages/first.htm* dans la zone d’édition URL du navigateur. Vous devez voir une page vide avec la légende de fenêtre "Balises HTML principales"

   Notez que les étiquettes sont affichées par paires et incluses entre crochets pointus. Les étiquettes ne respectent pas la casse, mais la mise en majuscules est souvent utilisée pour distinguer les étiquettes.

   La balise \<HTML > démarre le document et la balise \</HTML > le termine. Les balises de fin (pas toujours requises) sont les mêmes que les balises de début à la seule différence qu'une barre oblique (/) précède la balise. Ne doit contenir aucun espace entre le chevron (<) et le début de l’étiquette.

1. Commutateur au bloc-notes et après le \</head > de ligne, tapez :

```
<BODY>
    HTML is swell.
    Life is good.
</BODY>
```

1. À partir de la **fichier** menu, choisissez **enregistrer**.

1. Basculez vers votre navigateur et actualisez la page.

   Les mots apparaissent dans la zone cliente de votre fenêtre de navigateur. Notez que votre retour chariot est ignoré. Si vous souhaitez avoir un saut de ligne, vous devez inclure une balise `<BR>` après la première ligne.

   Pour toutes les étapes qui suivent, insérez le texte n’importe où entre \<corps > et  \< /corps > pour ajouter le corps de votre document.

9. Ajoutez un en-tête :

```
<H3>Here's the big picture</H3>
```

10. Ajoutez une image, en utilisant un fichier .gif enregistré dans le même répertoire que votre page :

```
<IMG src="yourfile.gif">
```

11. Ajoutez une liste :

```
<UL>Make me an unordered list.
<LI>One programmer</LI>
<LI>Ten SDKs</LI>
<LI>Great Internet Apps</LI>
</UL>
```

12. Pour numéroter la liste au lieu de cela, utilisez jumelées \<OL > et \</OL > balises à la place de la \<UL > et \</UL > balises.

Cela peut vous aider à démarrer. Si vous consultez une fonctionnalité intéressante sur une page web, déterminez comment elle a été créée en examinant la source HTML. Les éditeurs HTML tels que Microsoft Front Page peuvent être utilisés pour créer des pages simples et avancées.

Voici la source HTML complète pour le fichier que vous aviez créé :

```
<HTML>
<HEAD>
<TITLE>Top HTML Tags</TITLE>
</HEAD>
<BODY>
HTML is swell.<BR>
Life is good.
<H3>Here's the big picture</H3>
<IMG src="yourfile.gif">
<UL>Make me an unordered list.
<LI>One programmer</LI>
<LI>Ten SDKs</LI>
<LI>Great Internet Apps</LI>
</UL>
</BODY>
</HTML>
```

Pour une description complète des étiquettes, attributs et extensions, consultez la spécification du langage HTML (Hypertext Markup Language) :

[Dernière version publiée de HTML](https://www.w3.org/TR/html/) à W3C.org.

## <a name="see-also"></a>Voir aussi

[Notions de base de la programmation Internet MFC](../mfc/mfc-internet-programming-basics.md)
