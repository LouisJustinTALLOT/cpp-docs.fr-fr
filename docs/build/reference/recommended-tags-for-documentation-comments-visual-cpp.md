---
title: Tags recommandés pour les commentaires de documentation (commentaires de documentation CMD)
ms.date: 11/04/2016
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
ms.openlocfilehash: 1648d0eb019a3aad25641d7f6a7edd1ba26acf7e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336172"
---
# <a name="recommended-tags-for-documentation-comments"></a>Balises recommandées pour les commentaires de documentation

Le compilateur MSVC traitera les commentaires de documentation dans votre code et crée un fichier .xdc pour chaque compiland, et xdcmake.exe traitera les fichiers .xdc à un fichier .xml. Le traitement du fichier .xml pour créer une documentation est un détail qui doit être implémenté sur votre site.

Les balises sont traitées sur des constructions telles que les types et les membres de type.

Les balises doivent immédiatement précéder les types ou membres.

> [!NOTE]
> Les commentaires de documentation ne peuvent pas être appliqués à un espace de noms ni à une définition hors ligne pour les propriétés et les événements ; les commentaires de documentation doivent figurer sur les déclarations de classe.

Le compilateur traite toute balise représentant du code XML correct. Les balises suivantes fournissent les fonctionnalités couramment utilisées dans la documentation utilisateur :

||||
|-|-|-|
|[\<c>](c-visual-cpp.md)|[\<>de code](code-visual-cpp.md)|[\<exemple>](example-visual-cpp.md)|
|exception>1 [ \< ](exception-visual-cpp.md)|comprennent>1 [ \< ](include-visual-cpp.md)|[\<liste>](list-visual-cpp.md)|
|[\<para>](para-visual-cpp.md)|param>1 [ \< ](param-visual-cpp.md)|paramref>1 [ \< ](paramref-visual-cpp.md)|
|autorisation>1 [ \< ](permission-visual-cpp.md)|[\<remarques>](remarks-visual-cpp.md)|[\<retourne>](returns-visual-cpp.md)|
|voir>1 [ \< ](see-visual-cpp.md)|seealso>1 [ \< ](seealso-visual-cpp.md)|[\<>résumé](summary-visual-cpp.md)|
|[\<>de valeur](value-visual-cpp.md)|||

1. Le compilateur vérifie la syntaxe.

Dans la version actuelle, le compilateur `<paramref>`MSVC ne prend pas en charge , une balise qui est pris en charge par d’autres compilateurs Visual Studio. Visual C++ peut prendre en charge `<paramref>` dans une version ultérieure.

## <a name="see-also"></a>Voir aussi

[XML Documentation](xml-documentation-visual-cpp.md)
