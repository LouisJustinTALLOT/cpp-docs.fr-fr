---
title: /DEPENDENTLOADFLAG (Définir les indicateurs de charge dépendants par défaut)
description: L’option/DEPENDENTLOADFLAG définit les indicateurs de charge dépendants par défaut pour les DLL chargées par ce module.
ms.date: 01/22/2020
f1_keywords:
- dependentloadflag
helpviewer_keywords:
- LINK tool [C++], dependent load flags
- -DEPENDENTLOADFLAG linker option
- linker [C++], DEPENDENTLOADFLAG
- DEPENDENTLOADFLAG linker option
- /DEPENDENTLOADFLAG linker option
ms.openlocfilehash: 5e31a0d747e7186814cba3ae1c4cf243569d87a8
ms.sourcegitcommit: b67b08472b6f1ee8f1c5684bba7056d3e0fc745f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76725706"
---
# <a name="dependentloadflag-set-default-dependent-load-flags"></a>/DEPENDENTLOADFLAG (Définir les indicateurs de charge dépendants par défaut)

::: moniker range="vs-2015"

L’option **/DEPENDENTLOADFLAG** nécessite Visual Studio 2017 ou une version ultérieure.

::: moniker-end

::: moniker range=">=vs-2017"

Définit les indicateurs de charge par défaut utilisés lorsque le système d’exploitation résout les importations liées statiquement d’un module.

## <a name="syntax"></a>Syntaxe

> **/DEPENDENTLOADFLAG**[ __:__ *load_flags*]

### <a name="arguments"></a>Arguments

*load_flags*<br/>
Valeur entière facultative qui spécifie les indicateurs de charge à appliquer lors de la résolution des dépendances d’importation liées statiquement du module. La valeur par défaut est 0. Pour obtenir la liste des valeurs d’indicateur prises en charge, consultez les entrées `LOAD_LIBRARY_SEARCH_*` dans [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw).

## <a name="remarks"></a>Notes

Lorsque le système d’exploitation résout les importations liées statiquement d’un module, il utilise l' [ordre de recherche par défaut](/windows/win32/dlls/dynamic-link-library-search-order). Utilisez l’option **/DEPENDENTLOADFLAG** pour spécifier une valeur *load_flags* qui modifie le chemin de recherche utilisé pour résoudre ces importations. Sur les systèmes d’exploitation pris en charge, il modifie l’ordre de recherche de résolution d’importation statique, de la même façon que [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexa) lors de l’utilisation de `LOAD_LIBRARY_SEARCH` paramètres. Pour plus d’informations sur l’ordre de recherche défini par *load_flags*, consultez [Rechercher un ordre à l’aide d’indicateurs LOAD_LIBRARY_SEARCH](/windows/win32/dlls/dynamic-link-library-search-order#search-order-using-load_library_search-flags).

Cet indicateur peut être utilisé pour rendre plus difficile un vecteur d' [attaque de plantation de dll](/windows/win32/dlls/dynamic-link-library-security) . Par exemple, considérez une application qui a lié de manière statique une DLL :

- Une personne malveillante peut planter une DLL portant le même nom précédemment dans le chemin de recherche de résolution d’importation, comme le répertoire de l’application. Les répertoires protégés sont plus difficiles, mais pas impossibles, à modifier par un pirate.

- Si la DLL est absente des répertoires application,%Windows%\System32 et% Windows%, la résolution d’importation passe au répertoire actif. Une personne malveillante peut y planter une DLL.

Dans les deux cas, si vous spécifiez l’option de lien `/DEPENDENTLOADFLAG:0x800` (la valeur de l’indicateur `LOAD_LIBRARY_SEARCH_SYSTEM32`), le chemin de recherche de module est limité au répertoire%Windows%\System32. Il offre une protection contre les attaques sur les autres annuaires. Pour plus d’informations, consultez [sécurité de la bibliothèque de liens dynamiques](/windows/win32/dlls/dynamic-link-library-security).

Pour voir la valeur définie par l’option **/DEPENDENTLOADFLAG** dans n’importe quelle dll, utilisez la commande [DUMPBIN](dumpbin-reference.md) avec l’option [/LOADCONFIG](loadconfig.md) .

L’option **/DEPENDENTLOADFLAG** est une nouveauté de Visual Studio 2017. Elle s’applique uniquement aux applications qui s’exécutent sur Windows 10 RS1 et versions ultérieures. Cette option est ignorée par les autres systèmes d’exploitation qui exécutent l’application.

### <a name="to-set-the-dependentloadflag-linker-option-in-the-visual-studio-development-environment"></a>Pour définir l’option DEPENDENTLOADFLAG de l’éditeur de liens dans l’environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour obtenir des informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez **Propriétés de Configuration** > **éditeur de liens** > page de propriétés ligne de **commande** .

1. Entrez l’option dans **options supplémentaires**.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur l’éditeur de liens MSVC](linking.md)
- [Options de l’éditeur de liens MSVC](linker-options.md)
- [Lier implicitement un exécutable à une DLL](../linking-an-executable-to-a-dll.md#linking-implicitly)
- [Déterminer la méthode de liaison à utiliser](../linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)
- [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)
- [Ordre de recherche de la bibliothèque de liens dynamiques](/windows/win32/Dlls/dynamic-link-library-search-order)
- [Sécurité de la bibliothèque de liens dynamiques](/windows/win32/dlls/dynamic-link-library-security)

::: moniker-end
