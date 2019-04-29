---
title: Implications en matière de sécurité de la personnalisation
ms.date: 11/04/2016
helpviewer_keywords:
- security, MFC Feature Pack
- MFC Feature Pack, security
ms.assetid: 9be96b12-be38-43bd-a133-5d671265f7a1
ms.openlocfilehash: 9164983a6634e069195f3498bea56b595a2a2381
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308470"
---
# <a name="security-implications-of-customization"></a>Implications en matière de sécurité de la personnalisation

Cette rubrique présente une faille de sécurité potentielle dans MFC.

## <a name="potential-security-weakness"></a>Faille de sécurité potentielle

MFC permet à l’utilisateur personnaliser l’apparence d’une interface utilisateur d’applications, par exemple, l’apparence des boutons et des icônes. MFC prend également en charge les outils définis par l’utilisateur, qui permettent à l’utilisateur d’exécuter des commandes d’interpréteur de commandes. Une faille de sécurité se pose, car les paramètres personnalisés de l’application sont enregistrées dans le profil utilisateur dans le Registre. Toute personne peut accéder au Registre peut modifier ces paramètres et modifier l’apparence de l’application ou le comportement. Par exemple, un administrateur sur l’ordinateur peut emprunter l’identité d’un utilisateur en provoquant l’application l’utilisateur d’exécuter des programmes arbitraires (même à partir d’un partage réseau).

## <a name="workarounds"></a>Solutions

Nous recommandons une de ces trois méthodes pour fermer les vulnérabilités dans le Registre :

- Chiffrer les données qui y sont stockées

- Store les données dans un fichier sécurisé au lieu de dans le Registre.

   Pour effectuer l’une de ces deux premières méthodes, dérivez une classe de [CSettingsStore Class](../mfc/reference/csettingsstore-class.md) et substituer ses méthodes pour implémenter le chiffrement ou le stockage en dehors du Registre.

- Vous pouvez également désactiver des personnalisations dans votre application.

## <a name="see-also"></a>Voir aussi

[Personnalisation pour MFC](../mfc/customization-for-mfc.md)
