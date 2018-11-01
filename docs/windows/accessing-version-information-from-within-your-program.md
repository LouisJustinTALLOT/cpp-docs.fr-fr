---
title: L’accès aux informations de Version à partir de votre programme (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.version
helpviewer_keywords:
- VerQueryValue
- version information, accessing from within programs
- GetFileVersionInfo
- version information
ms.assetid: 18622333-d9e8-4309-9465-677cd10c79b1
ms.openlocfilehash: 028ea6126b75b914e7ff9a4ded2d08efa9d35b28
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644624"
---
# <a name="accessing-version-information-from-within-your-program-c"></a>L’accès aux informations de Version à partir de votre programme (C++)

### <a name="to-access-version-information-from-within-your-program"></a>Pour accéder aux informations de version à partir de votre programme

1. Si vous souhaitez accéder aux informations de version à partir de votre programme, utilisez les fonctions [GetFileVersionInfo](/windows/desktop/api/winver/nf-winver-getfileversioninfoa) et [VerQueryValue](/windows/desktop/api/winver/nf-winver-verqueryvaluea) .

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Éditeur d’informations sur la version](../windows/version-information-editor.md)<br/>
[Informations sur la version (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)