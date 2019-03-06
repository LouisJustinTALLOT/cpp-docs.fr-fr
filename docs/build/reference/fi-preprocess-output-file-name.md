---
title: /Fi (prétraiter le nom du fichier de sortie)
ms.date: 11/04/2016
f1_keywords:
- /Fi
helpviewer_keywords:
- Fi compiler option (C++)
- -Fi compiler option (C++)
- /Fi compiler option (C++)
- preprocessing output files, file name
ms.assetid: 6d0ba983-a8b7-41ec-84f5-b4688ef8efee
ms.openlocfilehash: 02d2a27f0a3d6b6aee6c2cd6f7161c9de718446d
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414021"
---
# <a name="fi-preprocess-output-file-name"></a>/Fi (prétraiter le nom du fichier de sortie)

Spécifie le nom du fichier de sortie auquel le [/P (Prétraiter dans un fichier)](../../build/reference/p-preprocess-to-a-file.md) option du compilateur écrit la sortie prétraitée.

## <a name="syntax"></a>Syntaxe

```
/Fipathname
```

#### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|`pathname`|Le nom et le chemin d’accès du fichier de sortie produits par le **/P** option du compilateur.|

## <a name="remarks"></a>Notes

Utilisez le **/Fi** option du compilateur en association avec le **/P** option du compilateur.

Si vous spécifiez uniquement un chemin d’accès pour le `pathname` paramètre, le nom de base du fichier source est utilisé comme nom de base du fichier de sortie prétraité. Le `pathname` paramètre ne nécessite pas une extension de nom de fichier particulier. Toutefois, une extension de « .i » est utilisée si vous ne spécifiez pas une extension de nom de fichier.

## <a name="example"></a>Exemple

La ligne de commande suivante prétraite PROGRAM.cpp, conserve les commentaires, ajoute [#line](../../preprocessor/hash-line-directive-c-cpp.md) directives et écrit le résultat dans le fichier MYPROCESS.i.

```
CL /P /FiMYPROCESS.I PROGRAM.CPP
```

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[/P (Prétraiter jusqu’à un fichier)](../../build/reference/p-preprocess-to-a-file.md)<br/>
[Spécification du nom de chemin](../../build/reference/specifying-the-pathname.md)
