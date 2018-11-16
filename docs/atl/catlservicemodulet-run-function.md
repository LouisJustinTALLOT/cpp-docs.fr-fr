---
title: CAtlServiceModuleT::Run, fonction
ms.date: 11/04/2016
f1_keywords:
- CServiceModule::Run
- CServiceModule.Run
- CSecurityDescriptor
helpviewer_keywords:
- ATL services, security
ms.assetid: 42c010f0-e60e-459c-a63b-a53a24cda93b
ms.openlocfilehash: 91b6465dd975a1e3227d1416f2b78a8abbd441ad
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694320"
---
# <a name="catlservicemoduletrun-function"></a>CAtlServiceModuleT::Run, fonction

`Run` contient des appels de `PreMessageLoop`, `RunMessageLoop`, et `PostMessageLoop`. Après avoir été appelée, `PreMessageLoop` tout d’abord stocke les ID de thread. du service Le service utilisera cet ID pour se fermer lui-même en envoyant le message WM_QUIT à l’aide de la fonction API Win32, [PostThreadMessage](/windows/desktop/api/winuser/nf-winuser-postthreadmessagea).

`PreMessageLoop` appelle ensuite `InitializeSecurity`. Par défaut, `InitializeSecurity` appels [CoInitializeSecurity](/windows/desktop/api/combaseapi/nf-combaseapi-coinitializesecurity) avec le descripteur de sécurité la valeur NULL, ce qui signifie que n’importe quel utilisateur a accès à votre objet.

Si vous ne souhaitez pas le service pour spécifier sa propre sécurité, substituez `PreMessageLoop` et n’appelez pas `InitializeSecurity`, COM avant de déterminer les paramètres de sécurité à partir du Registre. Un moyen pratique pour configurer les paramètres de Registre est avec la [DCOMCNFG](../atl/dcomcnfg.md) utilitaire décrit plus loin dans cette section.

Une fois que la sécurité est spécifiée, l’objet est enregistré avec COM afin que les nouveaux clients peuvent se connecter au programme. Enfin, le programme indique le Gestionnaire de contrôle des services (SCM) qu’il est en cours d’exécution et que le programme entre dans une boucle de message. Le programme continue de s’exécuter jusqu'à ce qu’il publie un message quit en cas d’arrêt du service.

## <a name="see-also"></a>Voir aussi

[Services](../atl/atl-services.md)<br/>
[CSecurityDesc, classe](../atl/reference/csecuritydesc-class.md)<br/>
[CSid, classe](../atl/reference/csid-class.md)<br/>
[CDacl, classe](../atl/reference/cdacl-class.md)<br/>
[CAtlServiceModuleT::Run](../atl/reference/catlservicemodulet-class.md#run)

