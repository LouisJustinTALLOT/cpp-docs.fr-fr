---
title: / DEPENDENTLOADFLAG (indicateurs de charge dépendants définis par défaut)
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
ms.openlocfilehash: 0b6d5099e90e4a4bf83874fe8e761280bc277830
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43688115"
---
# <a name="dependentloadflag-set-default-dependent-load-flags"></a>/ DEPENDENTLOADFLAG (indicateurs de charge dépendants définis par défaut)

Définit les indicateurs de charge par défaut utilisée lorsque `LoadLibrary` est utilisée pour charger la DLL.

## <a name="syntax"></a>Syntaxe

> **/ DEPENDENTLOADFLAG**[**:**_loadflags_]

### <a name="arguments"></a>Arguments

|||
|-|-|
*loadflags*|Une valeur d’entier 16 bits en « C »-style facultative dans décimal, octal avec un zéro non significatif ou hexadécimal avec un préfixe `0x`, qui spécifie les indicateurs de chargement dépendant à appliquer à tous les [LoadLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa) appels. La valeur par défaut est 0.

## <a name="remarks"></a>Notes

Cette option est une nouveauté de Visual Studio 2017 et s’applique uniquement aux applications qui s’exécutent sur Windows 10 RS1 et versions ultérieures. Cette option est ignorée par d’autres systèmes d’exploitation qui s’exécutent l’application.

Sur les systèmes d’exploitation pris en charge, cette option a pour effet de modifier les appels à `LoadLibrary("dependent.dll")` l’équivalent de `LoadLibraryEx("dependent.dll", 0, loadflags)`. Les appels à [LoadLibraryEx](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa) ne sont pas affectés. Cette option ne s’applique pas de manière récursive aux DLL chargées par votre application.

Cet indicateur peut servir à empêcher les DLL plantation des attaques. Par exemple, si une application utilise `LoadLibrary` pour charger une DLL dépendante, un agresseur pourrait installer une DLL portant le même nom dans le chemin de recherche utilisé par `LoadLibrary`, tels que le répertoire actif, qui peuvent être vérifié avant les répertoires système si le mode sans échec de la recherche DLL est désactivé. Mode sans échec de la recherche DLL place le répertoire actuel de l’utilisateur plus loin dans l’ordre de recherche et est activé par défaut sur Windows XP SP2 et versions ultérieures. Pour plus d’informations, consultez [Dynamic-Link Library Search Order](/windows/desktop/Dlls/dynamic-link-library-search-order).

Si vous spécifiez l’option de liaison `/DEPENDENTLOADFLAG:0xA00` (la valeur des indicateurs combinés `LOAD_LIBRARY_SEARCH_APPLICATION_DIR | LOAD_LIBRARY_SEARCH_SYSTEM32`), même si le mode sans échec de la recherche DLL est désactivé sur l’ordinateur de l’utilisateur, le chemin de recherche DLL est limité aux répertoires protégés qui sont plus difficiles pour une personne malveillante de modifier. Pour plus d’informations sur les indicateurs disponibles et leurs valeurs symboliques et numériques, consultez le *dwFlags* description du paramètre dans [LoadLibraryEx](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa).

### <a name="to-set-the-dependentloadflag-linker-option-in-the-visual-studio-development-environment"></a>Pour définir l’option de l’éditeur de liens DEPENDENTLOADFLAG dans l’environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **l’éditeur de liens** > **ligne de commande** page de propriétés.

1. Entrez l’option dans **des Options supplémentaires**.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

- [Définition des options de l’Éditeur de liens](setting-linker-options.md)
- [Options de l’éditeur de liens](linker-options.md)
- [Comment lier de manière implicite à une DLL](../linking-an-executable-to-a-dll.md#linking-implicitly)
- [Déterminer la méthode de liaison à utiliser](../linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)
- [LoadLibraryEx](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa)
- [Dynamic-Link Library Search Order](/windows/desktop/Dlls/dynamic-link-library-search-order)
