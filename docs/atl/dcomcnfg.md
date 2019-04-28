---
title: DCOMCNFG
ms.date: 11/04/2016
helpviewer_keywords:
- DCOMCNFG utility
- DCOM, configuring in ATL
ms.assetid: 5a8126e9-ef27-40fb-a66e-9dce8d1a7e80
ms.openlocfilehash: a389a46cd02b40cef46d687743fd3416cc4f3154
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62250782"
---
# <a name="dcomcnfg"></a>DCOMCNFG

DCOMCNFG est un utilitaire de Windows NT 4.0 qui vous permet de configurer différents paramètres spécifiques DCOM dans le Registre. La fenêtre DCOMCNFG comporte trois pages : Sécurité par défaut, les propriétés par défaut et les Applications. Sous Windows 2000, une quatrième page, protocoles par défaut, est présente.

## <a name="default-security-page"></a>Page de sécurité par défaut

Vous pouvez utiliser la page de sécurité par défaut pour spécifier les autorisations par défaut pour les objets sur le système. La page de sécurité par défaut comprend trois sections : Accès, Launch et Configuration. Pour modifier les valeurs par défaut d’une section, cliquez sur le correspondant **modifier la valeur par défaut** bouton. Ces paramètres de sécurité par défaut sont stockés dans le Registre sous `HKEY_LOCAL_MACHINE\Software\Microsoft\OLE`.

## <a name="default-protocols-page"></a>Page de protocoles par défaut

Cette page répertorie l’ensemble des protocoles réseau disponibles pour DCOM sur cet ordinateur. L’ordre reflète la priorité dans lequel ils seront utilisés ; le premier dans la liste a la priorité la plus élevée. Protocoles peuvent être ajoutés ou supprimés à partir de cette page.

## <a name="default-properties-page"></a>Page de propriétés par défaut

Dans la page de propriétés par défaut, vous devez sélectionner le **Activer Distributed COM sur cet ordinateur** case à cocher si vous souhaitez que les clients sur d’autres ordinateurs pour accéder aux objets COM en cours d’exécution sur cet ordinateur. En sélectionnant cette option définit la `HKEY_LOCAL_MACHINE\Software\Microsoft\OLE\EnableDCOM` valeur `Y`.

## <a name="applications-page"></a>Page des applications

Vous modifiez les paramètres pour un objet particulier avec la page Applications. Simplement sélectionner l’application à partir de la liste et cliquez sur le **propriétés** bouton. La fenêtre de propriétés comporte cinq pages :

- La page Général confirme l’application que vous utilisez.

- La page emplacement vous permet de spécifier où l’application doit s’exécuter lorsqu’un client appelle `CoCreateInstance` sur le CLSID concerné. Si vous sélectionnez le **exécuter l’application sur l’ordinateur suivant** case et entrez un nom d’ordinateur, puis un `RemoteServerName` valeur est ajoutée sous l’AppID pour cette application. Effacer la **exécuter l’application sur cet ordinateur** renomme de case à cocher le `LocalService` valeur `_LocalService` et, ce qui la désactive.

- La page de sécurité est similaire à la page sécurité par défaut dans la fenêtre DCOMCNFG, à ceci près que ces paramètres s’appliquent uniquement à l’application actuelle. Là encore, les paramètres sont stockés sous l’AppID pour cet objet.

- La page identifier identifie l’utilisateur qui est utilisé pour exécuter l’application.

- La page points de terminaison répertorie l’ensemble des protocoles et des points de terminaison disponibles pour une utilisation par les clients du serveur DCOM sélectionné.

## <a name="see-also"></a>Voir aussi

[Services](../atl/atl-services.md)
