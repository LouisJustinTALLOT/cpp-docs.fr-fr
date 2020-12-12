---
description: 'En savoir plus sur : CAtlServiceModuleT :: Run, fonction'
title: 'CAtlServiceModuleT :: Run, fonction'
ms.date: 11/04/2016
helpviewer_keywords:
- ATL services, security
ms.assetid: 42c010f0-e60e-459c-a63b-a53a24cda93b
ms.openlocfilehash: f8bba170236138f6491c49506bccd29bc23d9dec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148341"
---
# <a name="catlservicemoduletrun-function"></a>CAtlServiceModuleT :: Run, fonction

`Run` contient des appels à `PreMessageLoop` , `RunMessageLoop` et `PostMessageLoop` . Une fois appelé, `PreMessageLoop` stocke d’abord l’ID de thread du service. Le service utilisera cet ID pour se fermer lui-même en envoyant un message WM_QUIT à l’aide de la fonction API Win32 [PostThreadMessage](/windows/win32/api/winuser/nf-winuser-postthreadmessagew).

`PreMessageLoop` appelle ensuite `InitializeSecurity` . Par défaut, `InitializeSecurity` appelle [CoInitializeSecurity](/windows/win32/api/combaseapi/nf-combaseapi-coinitializesecurity) avec le descripteur de sécurité défini sur null, ce qui signifie que n’importe quel utilisateur a accès à votre objet.

Si vous ne souhaitez pas que le service spécifie sa propre sécurité, substituez `PreMessageLoop` et n’appelez pas `InitializeSecurity` , et com déterminera ensuite les paramètres de sécurité à partir du Registre. Un moyen pratique de configurer les paramètres du Registre consiste à utiliser l’utilitaire [DCOMCNFG](../atl/dcomcnfg.md) abordé plus loin dans cette section.

Une fois la sécurité spécifiée, l’objet est inscrit auprès de COM afin que les nouveaux clients puissent se connecter au programme. Enfin, le programme indique au gestionnaire de contrôle des services (SCM) qu’il exécute et le programme entre dans une boucle de message. Le programme continue de s’exécuter jusqu’à ce qu’il publie un message de fermeture lors de l’arrêt du service.

## <a name="see-also"></a>Voir aussi

[Services](../atl/atl-services.md)<br/>
[CSecurityDesc, classe](../atl/reference/csecuritydesc-class.md)<br/>
[CSid (classe)](../atl/reference/csid-class.md)<br/>
[CDacl, classe](../atl/reference/cdacl-class.md)<br/>
[CAtlServiceModuleT :: Run](../atl/reference/catlservicemodulet-class.md#run)
