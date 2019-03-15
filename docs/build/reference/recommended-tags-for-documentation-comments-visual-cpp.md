---
title: Balises recommandées pour commentaires de Documentation (commentaires de documentation C++)
ms.date: 11/04/2016
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
ms.openlocfilehash: adb8440dc07f8f3e193b58be6782859fbb8413e4
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825595"
---
# <a name="recommended-tags-for-documentation-comments"></a>Étiquettes recommandées pour les commentaires de documentation

Le compilateur MSVC traitera les commentaires de documentation dans votre code et crée un fichier .xdc pour chaque compiland et xdcmake.exe traitera les fichiers .xdc dans un fichier .xml. Le traitement du fichier .xml pour créer une documentation est un détail qui doit être implémenté sur votre site.

Les balises sont traitées sur des constructions telles que les types et les membres de type.

Les balises doivent immédiatement précéder les types ou membres.

> [!NOTE]
>  Les commentaires de documentation ne peuvent pas être appliqués à un espace de noms ni à une définition hors ligne pour les propriétés et les événements ; les commentaires de documentation doivent figurer sur les déclarations de classe.

Le compilateur traite toute balise représentant du code XML correct. Les balises suivantes fournissent les fonctionnalités couramment utilisées dans la documentation utilisateur :

||||
|-|-|-|
|[\<c>](c-visual-cpp.md)|[\<code>](code-visual-cpp.md)|[\<example>](example-visual-cpp.md)|
|[\<exception>](exception-visual-cpp.md)1|[\<include>](include-visual-cpp.md)1|[\<list>](list-visual-cpp.md)|
|[\<para>](para-visual-cpp.md)|[\<param>](param-visual-cpp.md)1|[\<paramref>](paramref-visual-cpp.md)1|
|[\<permission>](permission-visual-cpp.md)1|[\<remarks>](remarks-visual-cpp.md)|[\<returns>](returns-visual-cpp.md)|
|[\<see>](see-visual-cpp.md)1|[\<seealso>](seealso-visual-cpp.md)1|[\<summary>](summary-visual-cpp.md)|
|[\<value>](value-visual-cpp.md)|||

1. Le compilateur vérifie la syntaxe.

Dans la version actuelle, le compilateur MSVC ne prend pas en charge `<paramref>`, une balise qui est pris en charge par d’autres compilateurs Visual Studio. Visual C++ peut prendre en charge `<paramref>` dans une version ultérieure.

## <a name="see-also"></a>Voir aussi

[Documentation XML](xml-documentation-visual-cpp.md)