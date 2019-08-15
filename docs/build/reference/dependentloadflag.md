---
title: /DEPENDENTLOADFLAG (Définir les indicateurs de charge dépendants par défaut)
description: L’option/DEPENDENTLOADFLAG définit les indicateurs par défaut des DLL chargées à l’aide de LoadLibrary
ms.date: 05/18/2018
f1_keywords:
- dependentloadflag
helpviewer_keywords:
- LINK tool [C++], dependent load flags
- -DEPENDENTLOADFLAG linker option
- linker [C++], DEPENDENTLOADFLAG
- DEPENDENTLOADFLAG linker option
- /DEPENDENTLOADFLAG linker option
ms.openlocfilehash: 072fa1103d049c7d5c395ae88d268f3b47e20b4f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492958"
---
# <a name="dependentloadflag-set-default-dependent-load-flags"></a>/DEPENDENTLOADFLAG (Définir les indicateurs de charge dépendants par défaut)

Définit les indicateurs de charge par défaut `LoadLibrary` utilisés lorsque est utilisé pour charger des dll.

## <a name="syntax"></a>Syntaxe

> **/DEPENDENTLOADFLAG**[ **:** _loadflags_]

### <a name="arguments"></a>Arguments

*loadflags*<br/>
Valeur entière «C» de style «C» facultative dans Decimal, octal avec un zéro non significatif, ou hexadécimal avec un de `0x`début, qui spécifie les indicateurs de charge dépendants à appliquer à tous les appels [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) . La valeur par défaut est 0.

## <a name="remarks"></a>Notes

Cette option est nouvelle dans Visual Studio 2017 et s’applique uniquement aux applications qui s’exécutent sur Windows 10 RS1 et versions ultérieures. Cette option est ignorée par les autres systèmes d’exploitation qui exécutent l’application.

Sur les systèmes d’exploitation pris en charge, cette option a pour effet `LoadLibrary("dependent.dll")` de modifier les appels `LoadLibraryEx("dependent.dll", 0, loadflags)`à vers l’équivalent de. Les appels à [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) ne sont pas affectés. Cette option ne s’applique pas de manière récursive aux DLL chargées par votre application.

Cet indicateur peut être utilisé pour empêcher les attaques par plantation de DLL. Par exemple, si une application utilise `LoadLibrary` pour charger une dll dépendante, une personne malveillante peut planter une DLL portant le même nom dans le chemin `LoadLibrary`de recherche utilisé par, tel que le répertoire actif, qui peut être vérifiée avant les répertoires système si le mode de recherche de dll sécurisée est activée. Le mode de recherche de DLL sécurisé place le répertoire actuel de l’utilisateur plus tard dans l’ordre de recherche et est activé par défaut sur Windows XP SP2 et les versions ultérieures. Pour plus d’informations, consultez ordre de recherche de la [bibliothèque de liens dynamiques](/windows/win32/Dlls/dynamic-link-library-search-order).

Si vous spécifiez l’option `/DEPENDENTLOADFLAG:0xA00` de lien (la valeur des indicateurs `LOAD_LIBRARY_SEARCH_APPLICATION_DIR | LOAD_LIBRARY_SEARCH_SYSTEM32`combinés), même si le mode de recherche de dll sécurisé est désactivé sur l’ordinateur de l’utilisateur, le chemin de recherche de dll est limité aux répertoires protégés qui sont plus difficiles à modifiés. Pour plus d’informations sur les indicateurs disponibles et leurs valeurs symboliques et numériques, consultez la description du paramètre *dwFlags* dans [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw).

### <a name="to-set-the-dependentloadflag-linker-option-in-the-visual-studio-development-environment"></a>Pour définir l’option DEPENDENTLOADFLAG de l’éditeur de liens dans l’environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés**ligne de commande** de l'**éditeur de liens** >  **Propriétés** > de configuration.

1. Entrez l’option dans **options supplémentaires**.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur l’éditeur de liens MSVC](linking.md)
- [Options de l’éditeur de liens MSVC](linker-options.md)
- [Lier un exécutable à une DLL](../linking-an-executable-to-a-dll.md#linking-implicitly)
- [Lier un exécutable à une DLL](../linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)
- [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)
- [Ordre de recherche de la bibliothèque de liens dynamiques](/windows/win32/Dlls/dynamic-link-library-search-order)
