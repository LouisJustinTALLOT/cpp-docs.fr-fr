---
title: / DEPENDENTLOADFLAG (définir des indicateurs de chargement dépendant par défaut)
description: L’option /DEPENDENTLOADFLAG définit des indicateurs par défaut pour les DLL chargées à l’aide de LoadLibrary
ms.custom: ''
ms.date: 05/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- dependentloadflag
dev_langs:
- C++
helpviewer_keywords:
- LINK tool [C++], dependent load flags
- -DEPENDENTLOADFLAG linker option
- linker [C++], DEPENDENTLOADFLAG
- DEPENDENTLOADFLAG linker option
- /DEPENDENTLOADFLAG linker option
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a171f3c2edbbbf614a986ff78dd2405e734a1d1
ms.sourcegitcommit: d1f576a0f59678edc3d93508cf46485138332178
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753708"
---
# <a name="dependentloadflag-set-default-dependent-load-flags"></a>/ DEPENDENTLOADFLAG (définir des indicateurs de chargement dépendant par défaut)

Définit les indicateurs de charge par défaut utilisée lorsque `LoadLibrary` est utilisé pour charger la DLL.

## <a name="syntax"></a>Syntaxe

> **/ DEPENDENTLOADFLAG**[**:**_loadflags_]

### <a name="arguments"></a>Arguments

|||
|-|-|
*loadflags*|Valeur facultative « C » de type entier 16 bits en décimal, hexadécimal de début ou octal avec un zéro non significatif `0x`, qui spécifie les indicateurs de chargement dépendant à appliquer à tous les [LoadLibrary](https://go.microsoft.com/fwlink/p/?LinkID=259187) appels. La valeur par défaut est 0.

## <a name="remarks"></a>Notes

Cette option est une nouveauté de Visual Studio 2017 et s’applique uniquement aux applications qui s’exécutent sur Windows 10 RS1 et versions ultérieures. Cette option est ignorée par d’autres systèmes d’exploitation qui s’exécutent l’application.

Sur les systèmes d’exploitation pris en charge, cette option a pour effet de modifier les appels à `LoadLibrary("dependent.dll")` l’équivalent de `LoadLibraryEx("dependent.dll", 0, loadflags)`. Les appels à [LoadLibraryEx](https://go.microsoft.com/fwlink/p/?LinkID=236091) ne sont pas affectés. Cette option ne s’applique pas de manière récursive pour les DLL chargées par votre application.

Cet indicateur peut être utilisé pour empêcher les DLL plantation attaques. Par exemple, si une application utilise `LoadLibrary` pour charger une DLL dépendante, un agresseur peut installer une DLL portant le même nom dans le chemin de recherche utilisé par `LoadLibrary`, tels que le répertoire actif, ce qui peut être vérifié avant les répertoires du système si le mode sans échec de la recherche DLL est désactivé. Mode sans échec de la recherche DLL place le répertoire de l’utilisateur actuel plus loin dans l’ordre de recherche et est activé par défaut sur Windows XP SP2 et versions ultérieures. Pour plus d’informations, consultez [ordre de recherche de bibliothèque de liens dynamiques](https://msdn.microsoft.com/library/windows/desktop/ms682586.aspx).

Si vous spécifiez l’option de liaison `/DEPENDENTLOADFLAG:0xA00` (la valeur des indicateurs combinées `LOAD_LIBRARY_SEARCH_APPLICATION_DIR | LOAD_LIBRARY_SEARCH_SYSTEM32`), même si le mode sans échec de la recherche DLL est désactivé sur l’ordinateur, le chemin de recherche DLL est limité à des répertoires protégés qui sont plus difficiles pour un intrus de modification. Pour plus d’informations sur les indicateurs disponibles et leurs valeurs symboliques et numériques, consultez la *dwFlags* description du paramètre dans [LoadLibraryEx](https://go.microsoft.com/fwlink/p/?LinkID=236091).

### <a name="to-set-the-dependentloadflag-linker-option-in-the-visual-studio-development-environment"></a>Pour définir l’option de l’éditeur de liens DEPENDENTLOADFLAG dans l’environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **l’éditeur de liens** > **ligne de commande** page de propriétés.

1. Entrez l’option de **des Options supplémentaires**.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

- [Définition des options de l’Éditeur de liens](setting-linker-options.md)
- [Options de l’éditeur de liens](linker-options.md)
- [Comment lier de manière implicite à une DLL](../linking-an-executable-to-a-dll.md#linking-implicitly)
- [Déterminer la méthode de liaison à utiliser](../linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)
- [LoadLibrary](https://go.microsoft.com/fwlink/p/?LinkID=259187)
- [LoadLibraryEx](https://go.microsoft.com/fwlink/p/?LinkID=236091)
- [Ordre de recherche de bibliothèque de liens dynamiques](https://msdn.microsoft.com/library/windows/desktop/ms682586.aspx)
