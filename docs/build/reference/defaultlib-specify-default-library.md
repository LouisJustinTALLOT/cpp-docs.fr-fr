---
description: En savoir plus sur:/DEFAULTLIB (spécifier la bibliothèque par défaut)
title: /DEFAULTLIB (Spécifier la bibliothèque par défaut)
ms.date: 05/29/2018
f1_keywords:
- VC.Project.VCLinkerTool.DefaultLibraries
- /defaultlib
helpviewer_keywords:
- -DEFAULTLIB linker option
- DEFAULTLIB linker option
- /DEFAULTLIB linker option
- libraries, adding to list of
ms.assetid: 6af7ff49-c170-4a13-97e2-2b9ae2de20c9
ms.openlocfilehash: 9abaf158ed01b3e0a04d29c55d213c8749462c43
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201688"
---
# <a name="defaultlib-specify-default-library"></a>/DEFAULTLIB (Spécifier la bibliothèque par défaut)

Spécifiez une bibliothèque par défaut à rechercher pour résoudre les références externes.

## <a name="syntax"></a>Syntaxe

> **/DEFAULTLIB**:_bibliothèque_

### <a name="arguments"></a>Arguments

*Bibliothèque*<br/>
Nom d’une bibliothèque à rechercher lors de la résolution des références externes.

## <a name="remarks"></a>Notes

L’option **/DEFAULTLIB** ajoute une *bibliothèque* à la liste des bibliothèques qui lient les recherches lors de la résolution des références. Une bibliothèque spécifiée avec **/DEFAULTLIB** est recherchée après les bibliothèques spécifiées explicitement sur la ligne de commande et avant les bibliothèques par défaut nommées dans les fichiers. obj.

En cas d’utilisation sans arguments, l’option [/NODEFAULTLIB (ignorer toutes les bibliothèques par défaut)](nodefaultlib-ignore-libraries.md) remplace toutes les options **/DEFAULTLIB**:*Library* . L’option **/NODEFAULTLIB**:*Library* remplace **/DEFAULTLIB**:*Library* lorsque le même nom de *bibliothèque* est spécifié dans les deux.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande de l’éditeur de liens **Propriétés de configuration**  >    >   .

1. Dans **options supplémentaires**, entrez une option **/DEFAULTLIB**:*Library* pour chaque bibliothèque dans laquelle effectuer la recherche. Choisissez **OK** pour enregistrer vos modifications.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur l’éditeur de liens MSVC](linking.md)
- [Options de l’éditeur de liens MSVC](linker-options.md)
