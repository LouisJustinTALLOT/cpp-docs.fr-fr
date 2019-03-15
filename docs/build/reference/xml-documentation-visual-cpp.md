---
title: Documentation XML (Visual C++)
ms.date: 11/04/2016
helpviewer_keywords:
- XML documentation
- XML, documentation comments in source code
- comments, C++ source code files
- /// delimiter for C++ documentation
ms.assetid: a1aec1c5-b2d1-4c74-83ae-1dbbbb76b506
ms.openlocfilehash: d111d601d966ec5f863d62d9788654101a2ab56d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825527"
---
# <a name="xml-documentation-visual-c"></a>Documentation XML (Visual C++)

Dans Visual C++, vous pouvez ajouter des commentaires à votre code source qui sera traité dans un fichier .xml. Ce fichier peut ensuite être l’entrée d’un processus qui crée la documentation pour les classes dans votre code.

Dans un fichier de code Visual C++, les commentaires de documentation XML doivent être situés directement avant une méthode ou une définition de type. Les commentaires peuvent être utilisés pour renseigner la bulle d’informations Info express IntelliSense dans les scénarios suivants :

1. quand le code est compilé en tant que composant Windows Runtime avec un fichier .winmd associé

1. quand le code source est inclus dans le projet actif

1. dans une bibliothèque dont les déclarations de type et les implémentations se trouvent dans le même fichier d’en-tête

> [!NOTE]
>  Dans la version actuelle, les commentaires de code ne sont pas traités sur des modèles ni tout élément contenant un type de modèle (par exemple, une fonction qui prend un paramètre comme modèle). L’ajout de ces commentaires entraîne un comportement non défini.

Pour plus d’informations sur la création d’un fichier .xml avec des commentaires de documentation, consultez les rubriques suivantes.

|Pour obtenir des informations sur|Voir|
|---------------------------|---------|
|Options du compilateur à utiliser|[/doc](doc-process-documentation-comments-c-cpp.md)|
|Balises que vous pouvez utiliser pour fournir les fonctionnalités couramment utilisées dans la documentation|[Balises recommandées pour les commentaires de documentation](recommended-tags-for-documentation-comments-visual-cpp.md)|
|Chaînes d’ID que le compilateur produit pour identifier les constructions dans votre code|[Traitement du fichier .xml](dot-xml-file-processing.md)|
|Procédure pour délimiter les balises de documentation|[Délimiteurs pour les étiquettes de documentation Visual C++](delimiters-for-visual-cpp-documentation-tags.md)|
|Génération d’un fichier .xml à partir d’un ou de plusieurs fichiers .xdc|[Informations de référence sur XDCMake](xdcmake-reference.md)|
|Liens vers des informations sur XML par rapport aux zones des fonctionnalités Visual Studio|[XML dans Visual Studio](/visualstudio/xml-tools/xml-tools-in-visual-studio)|

Si vous devez placer des caractères spéciaux XML dans le texte d’un commentaire de documentation, vous devez utiliser des entités XML ou une section CDATA.

## <a name="see-also"></a>Voir aussi

[Extensions de composant pour les plateformes Runtime](../../windows/component-extensions-for-runtime-platforms.md)
