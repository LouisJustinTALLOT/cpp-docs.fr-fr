---
description: 'En savoir plus sur : prise en charge des contextes d’activation dans l’état du module MFC'
title: Prise en charge des contextes d'activation dans l'état du module MFC
ms.date: 11/04/2016
helpviewer_keywords:
- activation contexts [MFC]
- activation contexts [MFC], MFC support
ms.assetid: 1e49eea9-3620-46dd-bc5f-d664749567c7
ms.openlocfilehash: e7f7434824956ca2a62d75fbd50eb9dd5e01f34e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216468"
---
# <a name="support-for-activation-contexts-in-the-mfc-module-state"></a>Prise en charge des contextes d'activation dans l'état du module MFC

MFC crée un contexte d’activation à l’aide d’une ressource de manifeste fournie par le module utilisateur. Pour plus d’informations sur la façon dont les contextes d’activation sont créés, consultez les rubriques suivantes :

- [Contextes d’activation](/windows/win32/SbsCs/activation-contexts)

- [Manifestes d’application](/windows/win32/SbsCs/application-manifests)

- [Manifestes d’assembly](/windows/win32/SbsCs/assembly-manifests)

## <a name="remarks"></a>Notes

Lors de la lecture de ces SDK Windows rubriques, Notez que le mécanisme de contexte d’activation MFC ressemble au contexte d’activation SDK Windows, à ceci près que MFC n’utilise pas l’API de contexte d’activation SDK Windows.

Le contexte d’activation fonctionne dans les applications MFC, les dll utilisateur et les dll d’extension MFC des manières suivantes :

- Les applications MFC utilisent l’ID de ressource 1 pour leur ressource de manifeste. Dans ce cas, le MFC ne crée pas son propre contexte d’activation, mais utilise le contexte d’application par défaut.

- Les dll utilisateur MFC utilisent l’ID de ressource 2 pour leur ressource de manifeste. Ici, MFC crée un contexte d’activation pour chaque DLL d’utilisateur, de sorte que différentes dll utilisateur peuvent utiliser différentes versions des mêmes bibliothèques (par exemple, la bibliothèque de contrôles communs).

- Les dll d’extension MFC s’appuient sur leurs applications d’hébergement ou les dll utilisateur pour établir leur contexte d’activation.

Bien que l’état du contexte d’activation puisse être modifié à l’aide des processus décrits dans [utilisation de l’API de contexte](/windows/win32/SbsCs/using-the-activation-context-api)d’activation, l’utilisation du mécanisme de contexte d’activation MFC peut être utile lors du développement d’architectures de plug-in dll dans lesquelles il n’est pas facile (ou impossible) de basculer manuellement l’état d’activation avant et après les appels individuels aux plug-ins externes

Le contexte d’activation est créé dans [AfxWinInit](../mfc/reference/application-information-and-management.md#afxwininit). Il est détruit dans le `AFX_MODULE_STATE` destructeur. Un handle de contexte d’activation est conservé dans `AFX_MODULE_STATE` . ( `AFX_MODULE_STATE` est décrit dans [AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate).)

La macro [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) active et désactive le contexte d’activation. `AFX_MANAGE_STATE` est activé pour les bibliothèques MFC statiques, ainsi que les DLL MFC, pour permettre au code MFC de s’exécuter dans le contexte d’activation sélectionné par la DLL utilisateur.

## <a name="see-also"></a>Voir aussi

[Contextes d’activation](/windows/win32/SbsCs/activation-contexts)<br/>
[Manifestes d’application](/windows/win32/SbsCs/application-manifests)<br/>
[Manifestes d’assembly](/windows/win32/SbsCs/assembly-manifests)<br/>
[AfxWinInit](../mfc/reference/application-information-and-management.md#afxwininit)<br/>
[AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate)<br/>
[AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state)
