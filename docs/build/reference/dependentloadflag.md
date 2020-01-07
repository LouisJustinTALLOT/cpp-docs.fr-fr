---
title: /DEPENDENTLOADFLAG (Définir les indicateurs de charge dépendants par défaut)
description: L’option/DEPENDENTLOADFLAG définit les indicateurs par défaut des DLL chargées à l’aide de LoadLibrary
ms.date: 12/22/2018
f1_keywords:
- dependentloadflag
helpviewer_keywords:
- LINK tool [C++], dependent load flags
- -DEPENDENTLOADFLAG linker option
- linker [C++], DEPENDENTLOADFLAG
- DEPENDENTLOADFLAG linker option
- /DEPENDENTLOADFLAG linker option
ms.openlocfilehash: 3a403f22c88ccd3e25ba95c183656ad2ffafd05a
ms.sourcegitcommit: ef34a11cb04511221bf5c7b9f4f55ad91a7a603f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2019
ms.locfileid: "75329996"
---
# <a name="dependentloadflag-set-default-dependent-load-flags"></a>/DEPENDENTLOADFLAG (Définir les indicateurs de charge dépendants par défaut)

Définit les indicateurs de charge par défaut utilisés lorsque `LoadLibrary` est utilisé pour charger des dll.

## <a name="syntax"></a>Syntaxe

> **/DEPENDENTLOADFLAG**[ __:__ *load_flags*]

### <a name="arguments"></a>Arguments

*load_flags*<br/>
Valeur entière « C » de style « C » facultative dans le séparateur décimal, octal avec un zéro non significatif, ou hexadécimal avec un `0x`de début, qui spécifie les indicateurs de charge dépendants à appliquer à tous les appels [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) . La valeur par défaut est 0.

## <a name="remarks"></a>Notes

Cette option est une nouveauté de Visual Studio 2017. Elle s’applique uniquement aux applications qui s’exécutent sur Windows 10 RS1 et versions ultérieures. Cette option est ignorée par les autres systèmes d’exploitation qui exécutent l’application.

Sur les systèmes d’exploitation pris en charge, cette option a pour effet de modifier les appels à `LoadLibrary("dependent.dll")` à l’équivalent de `LoadLibraryEx("dependent.dll", 0, load_flags)`. Les appels à [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) ne sont pas affectés. Cette option ne s’applique pas de manière récursive aux DLL chargées par votre application.

Cet indicateur peut être utilisé pour rendre [les attaques de plantation de dll](/windows/win32/dlls/dynamic-link-library-security) plus difficiles. Par exemple, si une application utilise `LoadLibrary` pour charger une DLL dépendante, une personne malveillante peut planter une DLL portant le même nom dans le chemin de recherche utilisé par `LoadLibrary`, telle que le répertoire actif, qui peut être vérifiée avant les répertoires système si le mode de recherche de DLL sécurisé est désactivé. Le mode de recherche de DLL sécurisé place le répertoire actuel de l’utilisateur plus tard dans l’ordre de recherche et est activé par défaut sur Windows XP SP2 et les versions ultérieures. Pour plus d’informations, consultez ordre de recherche de la [bibliothèque de liens dynamiques](/windows/win32/Dlls/dynamic-link-library-search-order).

Si vous spécifiez l’option de lien `/DEPENDENTLOADFLAG:0xA00` (la valeur des indicateurs combinés `LOAD_LIBRARY_SEARCH_APPLICATION_DIR | LOAD_LIBRARY_SEARCH_SYSTEM32`), même si le mode de recherche de DLL sécurisé est désactivé sur l’ordinateur de l’utilisateur, le chemin de recherche de la DLL est limité au répertoire de l’application, suivi du répertoire%Windows%\System32. Une option de `/DEPENDENTLOADFLAG:0x800` est encore plus restrictive et limite la recherche au répertoire%Windows%\System32. Les répertoires protégés sont plus difficiles, mais pas impossibles, à modifier par un pirate. Pour plus d’informations sur les indicateurs disponibles et leurs valeurs symboliques et numériques, consultez la description du paramètre *dwFlags* dans [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw). Pour plus d’informations sur l’ordre de recherche utilisé lorsque divers indicateurs de charge dépendants sont utilisés, consultez [Rechercher un ordre à l’aide d’indicateurs LOAD_LIBRARY_SEARCH](/windows/win32/dlls/dynamic-link-library-search-order#search-order-using-load_library_search-flags).

### <a name="to-set-the-dependentloadflag-linker-option-in-the-visual-studio-development-environment"></a>Pour définir l’option DEPENDENTLOADFLAG de l’éditeur de liens dans l’environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez **Propriétés de Configuration** > **éditeur de liens** > page de propriétés ligne de **commande** .

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
