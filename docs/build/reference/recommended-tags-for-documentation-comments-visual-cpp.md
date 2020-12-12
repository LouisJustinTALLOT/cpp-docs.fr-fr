---
description: 'En savoir plus sur : Balises recommandées pour les commentaires de documentation'
title: Balises recommandées pour les commentaires de documentation (commentaires de documentation C++)
ms.date: 11/04/2016
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
ms.openlocfilehash: 34bae4043231abed87770aec252303bd99707afe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225347"
---
# <a name="recommended-tags-for-documentation-comments"></a>Balises recommandées pour les commentaires de documentation

Le compilateur MSVC traitera les commentaires de documentation dans votre code et créera un fichier. XDC pour chaque compiland, et xdcmake.exe traitera les fichiers. XDC dans un fichier. Xml. Le traitement du fichier .xml pour créer une documentation est un détail qui doit être implémenté sur votre site.

Les balises sont traitées sur des constructions telles que les types et les membres de type.

Les balises doivent immédiatement précéder les types ou membres.

> [!NOTE]
> Les commentaires de documentation ne peuvent pas être appliqués à un espace de noms ni à une définition hors ligne pour les propriétés et les événements ; les commentaires de documentation doivent figurer sur les déclarations de classe.

Le compilateur traite toute balise représentant du code XML correct. Les balises suivantes fournissent les fonctionnalités couramment utilisées dans la documentation utilisateur :

[`<c>`](c-visual-cpp.md)
[`<code>`](code-visual-cpp.md)
[`<example>`](example-visual-cpp.md)
[`<exception>`](exception-visual-cpp.md)<sup></sup> 
 1 [`<include>`](include-visual-cpp.md) <sup></sup> 
 [`<list>`](list-visual-cpp.md) 1 
 [`<para>`](para-visual-cpp.md) 
 [`<param>`](param-visual-cpp.md) <sup></sup> 
 1 [`<paramref>`](paramref-visual-cpp.md) <sup></sup> 
 1 [`<permission>`](permission-visual-cpp.md) <sup></sup> 
 [`<remarks>`](remarks-visual-cpp.md) 1 
 [`<returns>`](returns-visual-cpp.md) 
 [`<see>`](see-visual-cpp.md) <sup></sup> 
 1 [`<seealso>`](seealso-visual-cpp.md) <sup>1</sup>
[`<summary>`](summary-visual-cpp.md)
[`<value>`](value-visual-cpp.md)

1. Le compilateur vérifie la syntaxe.

Dans la version actuelle, le compilateur MSVC ne prend pas en charge `<paramref>` , une balise prise en charge par d’autres compilateurs Visual Studio. Visual C++ peut prendre en charge `<paramref>` dans une version ultérieure.

## <a name="see-also"></a>Voir aussi

[Documentation XML](xml-documentation-visual-cpp.md)
