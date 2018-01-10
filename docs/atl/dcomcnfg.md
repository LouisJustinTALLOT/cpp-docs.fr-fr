---
title: DCOMCNFG | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DCOMCNFG
dev_langs: C++
helpviewer_keywords:
- DCOMCNFG utility
- DCOM, configuring in ATL
ms.assetid: 5a8126e9-ef27-40fb-a66e-9dce8d1a7e80
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f40b372666ba2b623450eb0e58a6c0ff372559ec
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="dcomcnfg"></a>DCOMCNFG
**DCOMCNFG** est un utilitaire Windows NT 4.0 qui permet de configurer différents paramètres spécifiques DCOM dans le Registre. Le **DCOMCNFG** fenêtre comporte trois pages : sécurité par défaut, les propriétés par défaut et les Applications. Sous Windows 2000, une quatrième page, protocoles par défaut, est présente.  
  
## <a name="default-security-page"></a>Page de sécurité par défaut  
 Vous pouvez utiliser la page de sécurité par défaut pour spécifier les autorisations par défaut pour les objets sur le système. La page sécurité par défaut comprend trois sections : accès, de démarrage et de Configuration. Pour modifier les valeurs par défaut d’une section, cliquez sur le correspondant **modifier** bouton. Ces paramètres de sécurité par défaut sont stockés dans le Registre sous `HKEY_LOCAL_MACHINE\Software\Microsoft\OLE`.  
  
## <a name="default-protocols-page"></a>Page protocoles par défaut  
 Cette page répertorie l’ensemble des protocoles réseau disponibles pour DCOM sur cet ordinateur. L’ordre reflète la priorité dans lequel ils seront utilisés ; le premier dans la liste a la priorité la plus élevée. Protocoles peuvent être ajoutés ou supprimés à partir de cette page.  
  
## <a name="default-properties-page"></a>Page de propriétés par défaut  
 Dans la page de propriétés par défaut, vous devez sélectionner le **Activer Distributed COM sur cet ordinateur** case à cocher si vous souhaitez que les clients sur d’autres ordinateurs pour accéder aux objets COM en cours d’exécution sur cet ordinateur. En sélectionnant cette option définit la `HKEY_LOCAL_MACHINE\Software\Microsoft\OLE\EnableDCOM` valeur `Y`.  
  
## <a name="applications-page"></a>Page des applications  
 Vous modifiez les paramètres d’un objet particulier à la page des Applications. Simplement sélectionner l’application à partir de la liste et cliquez sur le **propriétés** bouton. La fenêtre Propriétés comprend cinq pages :  
  
-   La page Général confirme l’application que vous utilisez.  
  
-   La page emplacement vous permet de spécifier où l’application doit s’exécuter lorsqu’un client appelle `CoCreateInstance` sur le CLSID concerné. Si vous sélectionnez le **exécuter l’application sur l’ordinateur suivant** case à cocher et entrez un nom d’ordinateur, puis un `RemoteServerName` valeur est ajoutée sous l’AppID pour cette application. Effacer la **exécuter l’application sur cet ordinateur** changements de noms de case à cocher le `LocalService` valeur `_LocalService` et, ce qui la désactive.  
  
-   La page sécurité est similaire à la sécurité par défaut de page trouvée dans le **DCOMCNFG** fenêtre, à ceci près que ces paramètres s’appliquent uniquement à l’application actuelle. Là encore, les paramètres sont stockés sous l’AppID pour cet objet.  
  
-   La page identifier identifie l’utilisateur qui est utilisé pour exécuter l’application.  
  
-   La page points de terminaison répertorie l’ensemble de protocoles et de points de terminaison disponibles pour une utilisation par les clients du serveur DCOM sélectionné.  
  
## <a name="see-also"></a>Voir aussi  
 [Services](../atl/atl-services.md)

