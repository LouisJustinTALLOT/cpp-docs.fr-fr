---
description: 'En savoir plus sur : documentation XML (Visual C++)'
title: Documentation XML (Visual C++)
ms.date: 11/04/2016
helpviewer_keywords:
- XML documentation
- XML, documentation comments in source code
- comments, C++ source code files
- /// delimiter for C++ documentation
ms.assetid: a1aec1c5-b2d1-4c74-83ae-1dbbbb76b506
ms.openlocfilehash: 762380d08483292866cb96b34be4d85f7a2f510a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97260941"
---
# <a name="xml-documentation-visual-c"></a>Documentation XML (Visual C++)

Dans Visual C++, vous pouvez ajouter des commentaires à votre code source qui sera traité dans un fichier .xml. Ce fichier peut ensuite être l’entrée d’un processus qui crée la documentation pour les classes dans votre code.

Dans un fichier de code Visual C++, les commentaires de documentation XML doivent être situés directement avant une méthode ou une définition de type. Les commentaires peuvent être utilisés pour renseigner la bulle d’informations Info express IntelliSense dans les scénarios suivants :

1. quand le code est compilé en tant que composant Windows Runtime avec un fichier .winmd associé

1. quand le code source est inclus dans le projet actif

1. dans une bibliothèque dont les déclarations de type et les implémentations se trouvent dans le même fichier d’en-tête

> [!NOTE]
> Dans la version actuelle, les commentaires de code ne sont pas traités sur des modèles ni tout élément contenant un type de modèle (par exemple, une fonction qui prend un paramètre comme modèle). L’ajout de ces commentaires entraîne un comportement non défini.

Pour plus d’informations sur la création d’un fichier .xml avec des commentaires de documentation, consultez les rubriques suivantes.

|Pour obtenir des informations sur|Consultez|
|---------------------------|---------|
|Options du compilateur à utiliser|[/doc](doc-process-documentation-comments-c-cpp.md)|
|Balises que vous pouvez utiliser pour fournir les fonctionnalités couramment utilisées dans la documentation|[Balises recommandées pour les commentaires de documentation](recommended-tags-for-documentation-comments-visual-cpp.md)|
|Chaînes d’ID que le compilateur produit pour identifier les constructions dans votre code|[Traitement du fichier. Xml](dot-xml-file-processing.md)|
|Procédure pour délimiter les balises de documentation|[Délimiteurs pour les étiquettes de documentation Visual C++](delimiters-for-visual-cpp-documentation-tags.md)|
|Génération d’un fichier .xml à partir d’un ou de plusieurs fichiers .xdc|[Référence XDCMake](xdcmake-reference.md)|
|Liens vers des informations sur XML par rapport aux zones des fonctionnalités Visual Studio|[XML dans Visual Studio](/visualstudio/xml-tools/xml-tools-in-visual-studio)|

Si vous devez placer des caractères spéciaux XML dans le texte d’un commentaire de documentation, vous devez utiliser des entités XML ou une section CDATA.

## <a name="see-also"></a>Voir aussi

[Extensions de composant pour les plateformes Runtime](../../extensions/component-extensions-for-runtime-platforms.md)
