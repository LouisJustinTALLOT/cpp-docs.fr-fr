---
description: 'En savoir plus sur : DCOMCNFG'
title: DCOMCNFG
ms.date: 11/04/2016
helpviewer_keywords:
- DCOMCNFG utility
- DCOM, configuring in ATL
ms.assetid: 5a8126e9-ef27-40fb-a66e-9dce8d1a7e80
ms.openlocfilehash: d99b0018d63cedbccaf57ec4cadeb649f390dcf1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97153159"
---
# <a name="dcomcnfg"></a>DCOMCNFG

DCOMCNFG est un utilitaire Windows NT 4,0 qui vous permet de configurer divers paramètres propres à DCOM dans le registre. La fenêtre DCOMCNFG comporte trois pages : sécurité par défaut, propriétés par défaut et applications. Sous Windows 2000 une quatrième page, protocoles par défaut, est présente.

## <a name="default-security-page"></a>Page sécurité par défaut

Vous pouvez utiliser la page sécurité par défaut pour spécifier les autorisations par défaut pour les objets sur le système. La page sécurité par défaut comporte trois sections : accès, lancement et configuration. Pour modifier les valeurs par défaut d’une section, cliquez sur le bouton **modifier par défaut** correspondant. Ces paramètres de sécurité par défaut sont stockés dans le Registre sous `HKEY_LOCAL_MACHINE\Software\Microsoft\OLE` .

## <a name="default-protocols-page"></a>Page protocoles par défaut

Cette page répertorie l’ensemble des protocoles réseau disponibles pour DCOM sur cet ordinateur. L’ordre reflète la priorité dans laquelle elles seront utilisées ; la première dans la liste a la priorité la plus élevée. Vous pouvez ajouter ou supprimer des protocoles à partir de cette page.

## <a name="default-properties-page"></a>Page de propriétés par défaut

Sur la page Propriétés par défaut, vous devez activer la case à cocher **activer COM distribué sur cet ordinateur** si vous souhaitez que les clients d’autres ordinateurs accèdent aux objets com en cours d’exécution sur cet ordinateur. La sélection de cette option affecte la `HKEY_LOCAL_MACHINE\Software\Microsoft\OLE\EnableDCOM` valeur à `Y` .

## <a name="applications-page"></a>Page des applications

Vous modifiez les paramètres d’un objet particulier à l’aide de la page applications. Sélectionnez simplement l’application dans la liste et cliquez sur le bouton **Propriétés** . Le Fenêtre Propriétés contient cinq pages :

- La page général confirme l’application avec laquelle vous travaillez.

- La page emplacement vous permet de spécifier l’emplacement où l’application doit s’exécuter lorsqu’un client appelle `CoCreateInstance` sur le CLSID approprié. Si vous activez la case à cocher **exécuter l’application sur l’ordinateur suivant** et que vous entrez un nom d’ordinateur, une `RemoteServerName` valeur est ajoutée sous l’AppID pour cette application. Si vous désactivez la case à cocher **exécuter l’application sur cet ordinateur** , la valeur est renommée `LocalService` `_LocalService` et, par conséquent, elle est désactivée.

- La page sécurité est similaire à la page sécurité par défaut qui se trouve dans la fenêtre DCOMCNFG, sauf que ces paramètres s’appliquent uniquement à l’application actuelle. Là encore, les paramètres sont stockés sous l’AppID pour cet objet.

- La page identifier identifie l’utilisateur qui est utilisé pour exécuter l’application.

- La page points de terminaison répertorie le jeu de protocoles et de points de terminaison pouvant être utilisés par les clients du serveur DCOM sélectionné.

## <a name="see-also"></a>Voir aussi

[Services](../atl/atl-services.md)
