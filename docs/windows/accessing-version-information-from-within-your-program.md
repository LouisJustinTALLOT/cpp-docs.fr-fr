---
title: L’accès aux informations de Version à partir de votre programme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.version
dev_langs:
- C++
helpviewer_keywords:
- VerQueryValue
- version information, accessing from within programs
- GetFileVersionInfo
- version information
ms.assetid: 18622333-d9e8-4309-9465-677cd10c79b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 79520523ebeda2cb0260d1bc79d0b6b35d33aa23
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39646957"
---
# <a name="accessing-version-information-from-within-your-program"></a>Accès aux informations de version à partir de votre programme
### <a name="to-access-version-information-from-within-your-program"></a>Pour accéder aux informations de version à partir de votre programme  
  
Si vous souhaitez accéder aux informations de version à partir de votre programme, utilisez les fonctions [GetFileVersionInfo](http://msdn.microsoft.com/library/windows/desktop/ms647003.aspx) et [VerQueryValue](http://msdn.microsoft.com/library/windows/desktop/ms647464.aspx) .  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Configuration requise
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur d’informations de version](../windows/version-information-editor.md)   
 [Informations de version (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)