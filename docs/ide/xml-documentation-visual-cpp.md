---
title: Documentation XML (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- XML documentation
- XML, documentation comments in source code
- comments, C++ source code files
- /// delimiter for C++ documentation
ms.assetid: a1aec1c5-b2d1-4c74-83ae-1dbbbb76b506
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de3df01d9e9bf5d63b4445956e4656687d0f4f2c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412286"
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
|Options du compilateur à utiliser|[/doc](../build/reference/doc-process-documentation-comments-c-cpp.md)|
|Balises que vous pouvez utiliser pour fournir les fonctionnalités couramment utilisées dans la documentation|[Balises recommandées pour les commentaires de documentation](../ide/recommended-tags-for-documentation-comments-visual-cpp.md)|
|Chaînes d’ID que le compilateur produit pour identifier les constructions dans votre code|[Traitement du fichier .xml](../ide/dot-xml-file-processing.md)|
|Procédure pour délimiter les balises de documentation|[Délimiteurs pour les étiquettes de documentation Visual C++](../ide/delimiters-for-visual-cpp-documentation-tags.md)|
|Génération d’un fichier .xml à partir d’un ou de plusieurs fichiers .xdc|[Informations de référence sur XDCMake](../ide/xdcmake-reference.md)|
|Liens vers des informations sur XML par rapport aux zones des fonctionnalités Visual Studio|[XML dans Visual Studio](/visualstudio/xml-tools/xml-tools-in-visual-studio)|

Si vous devez placer des caractères spéciaux XML dans le texte d’un commentaire de documentation, vous devez utiliser des entités XML ou une section CDATA.

## <a name="see-also"></a>Voir aussi

[Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)