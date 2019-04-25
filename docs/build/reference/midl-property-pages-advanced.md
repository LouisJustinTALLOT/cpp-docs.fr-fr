---
title: 'Pages de propriétés MIDL : Avancé'
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCMidlTool.ErrorCheckBounds
- VC.Project.VCMidlTool.ErrorCheckStubData
- VC.Project.VCMidlTool.ErrorCheckAllocations
- VC.Project.VCMidlTool.CPreprocessOptions
- VC.Project.VCMidlTool.UndefinePreprocessorDefinitions
- VC.Project.VCMidlTool.EnableErrorChecks
- VC.Project.VCMidlTool.RedirectOutputAndErrors
- VC.Project.VCMidlTool.ErrorCheckEnumRange
- VC.Project.VCMidlTool.StructMemberAlignment
- VC.Project.VCMidlTool.ErrorCheckRefPointers
- VC.Project.VCMidlTool.ValidateParameters
helpviewer_keywords:
- MIDL, property pages
ms.assetid: d1c92e01-f403-4ed6-ab45-4043a3c9c6bb
ms.openlocfilehash: 350563d140823910667812930f9283c7640cc1ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321473"
---
# <a name="midl-property-pages-advanced"></a>Pages de propriétés MIDL : Avancé

La page de propriétés **Avancé** du dossier **MIDL** spécifie les options du compilateur MIDL suivantes :

- Activation de la vérification d’erreurs ([/error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- Vérification des allocations ([/error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- Vérification des limites ([/error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- Vérification de la plage Enum ([/error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- Vérification des pointeurs de référence ([/error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- Vérification des données stub ([/error](https://msdn.microsoft.com/library/windows/desktop/aa367324))

- Validation des paramètres ([/robust](https://msdn.microsoft.com/library/windows/desktop/aa367363)) \*

- Alignement des membres de la structure ([/Zp](https://msdn.microsoft.com/library/windows/desktop/aa367388))

- Redirection de la sortie ([/o](https://msdn.microsoft.com/library/windows/desktop/aa367351))

- Options de préprocesseur C ([/cpp_opt](https://msdn.microsoft.com/library/windows/desktop/aa367318))

- Définitions de préprocesseur non définies ([/U](https://msdn.microsoft.com/library/windows/desktop/aa367373))

\* /robust peut être utilisé uniquement lors de la génération sur un ordinateur Windows 2000 ou ultérieur. Si vous générez un projet ATL et souhaitez utiliser /robust, modifiez cette ligne dans le fichier dlldatax.c :

```
#define _WIN32_WINNT 0x0400   //for Windows NT 4.0 or Windows 95 with DCOM
to
#define _WIN32_WINNT 0x0500   //for Windows NT 4.0 or Windows 95 with DCOM
```

Pour plus d’informations sur la façon d’accéder à la **avancé** page de propriétés dans le **MIDL** dossier, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

Pour plus d’informations sur l’accès par programmation aux options MIDL des projets C++, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool>.

## <a name="see-also"></a>Voir aussi

[MIDL, page de propriétés](midl-property-pages.md)
