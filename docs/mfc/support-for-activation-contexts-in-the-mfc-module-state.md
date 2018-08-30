---
title: Prise en charge des contextes d’Activation dans l’état du Module MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- activation contexts [MFC]
- activation contexts [MFC], MFC support
ms.assetid: 1e49eea9-3620-46dd-bc5f-d664749567c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6116452a3fa0fabc2b2f458c4c597e103607aafe
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43217712"
---
# <a name="support-for-activation-contexts-in-the-mfc-module-state"></a>Prise en charge des contextes d'activation dans l'état du module MFC
MFC crée un contexte d’activation à l’aide d’une ressource de manifeste fournie par le module de l’utilisateur. Pour plus d’informations sur la création des contextes d’activation, consultez les rubriques suivantes :  
  
-   [Contextes d’activation](/windows/desktop/SbsCs/activation-contexts)  
  
-   [Manifestes d’application](/windows/desktop/SbsCs/application-manifests)  
  
-   [Manifestes d’assembly](/windows/desktop/SbsCs/assembly-manifests)  
  
## <a name="remarks"></a>Notes  
 Lorsque vous lisez ces rubriques du Kit de développement logiciel Windows, notez que le mécanisme de contexte d’activation MFC ressemble au contexte d’activation de Windows SDK, à ceci près que MFC n’utilise pas l’API de contexte d’Activation de Windows SDK.  
  
 Contexte d’activation fonctionne dans les applications MFC, les DLL de l’utilisateur et les DLL d’extension MFC comme suit :  
  
-   Applications de MFC utilisent des ID de ressource 1 pour leurs ressources de manifeste. Dans ce cas, la bibliothèque MFC ne crée pas de son propre contexte d’activation, mais utilise le contexte de l’application par défaut.  
  
-   Utilisateur MFC DLL utiliser l’ID de ressource 2 pour leurs ressources de manifeste. Ici, MFC crée un contexte d’activation pour chaque DLL de l’utilisateur, afin de l’autre utilisateur DLL peut utiliser différentes versions des mêmes bibliothèques (par exemple, la bibliothèque de contrôles communs).  
  
-   DLL d’extension MFC s’appuient sur leurs applications ou utilisateur DLL hébergement pour établir leur contexte d’activation.  
  
 Bien que l’état de contexte d’activation peut être modifiée à l’aide de processus décrits sous [à l’aide de l’API de contexte d’Activation](/windows/desktop/SbsCs/using-the-activation-context-api), à l’aide du mécanisme de contexte d’activation MFC peut être utile lors du développement d’architectures de plug-in basées sur les DLL où il n’est pas facile (ou n’est pas possible) pour basculer manuellement l’état d’activation avant et après les appels individuels aux plug-ins externes.  
  
 Le contexte d’activation est créé dans [AfxWinInit](../mfc/reference/application-information-and-management.md#afxwininit). Il est détruit dans le `AFX_MODULE_STATE` destructeur. Un handle de contexte d’activation est conservé dans `AFX_MODULE_STATE`. (`AFX_MODULE_STATE` est décrite dans [AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate).)  
  
 Le [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) macro active et désactive le contexte d’activation. `AFX_MANAGE_STATE` est activé pour les bibliothèques statiques MFC, ainsi que les DLL MFC, pour permettre au code MFC à exécuter dans le contexte d’activation approprié sélectionné par la DLL de l’utilisateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Contextes d’activation](/windows/desktop/SbsCs/activation-contexts)   
 [Manifestes d’application](/windows/desktop/SbsCs/application-manifests)   
 [Manifestes d’assembly](/windows/desktop/SbsCs/assembly-manifests)   
 [AfxWinInit](../mfc/reference/application-information-and-management.md#afxwininit)   
 [AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate)   
 [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state)

