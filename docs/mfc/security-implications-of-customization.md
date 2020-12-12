---
description: 'En savoir plus sur : implications sur la sécurité de la personnalisation'
title: Implications en matière de sécurité de la personnalisation
ms.date: 11/04/2016
helpviewer_keywords:
- security, MFC Feature Pack
- MFC Feature Pack, security
ms.assetid: 9be96b12-be38-43bd-a133-5d671265f7a1
ms.openlocfilehash: 64a1029dd3486e3cd653f5e692aa1a14ba6f82b5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217755"
---
# <a name="security-implications-of-customization"></a>Implications en matière de sécurité de la personnalisation

Cette rubrique décrit une faille de sécurité potentielle dans MFC.

## <a name="potential-security-weakness"></a>Faille de sécurité potentielle

MFC permet à l’utilisateur de personnaliser l’apparence d’une interface utilisateur de l’application, par exemple, l’apparence des boutons et des icônes. MFC prend également en charge les outils définis par l’utilisateur, qui permettent à l’utilisateur d’exécuter des commandes shell. Une faille de sécurité se produit parce que les paramètres personnalisés de l’application sont enregistrés dans le profil utilisateur dans le registre. Toute personne pouvant accéder au registre peut modifier ces paramètres et modifier l’apparence ou le comportement de l’application. Par exemple, un administrateur sur l’ordinateur peut emprunter l’identité d’un utilisateur en forçant l’application de l’utilisateur à exécuter des programmes arbitraires (même à partir d’un partage réseau).

## <a name="workarounds"></a>Solutions de contournement

Nous vous recommandons d’utiliser l’une des trois méthodes suivantes pour fermer les vulnérabilités dans le registre :

- Chiffrer les données qui y sont stockées

- Stockez les données dans un fichier sécurisé plutôt que dans le registre.

   Pour effectuer l’une des deux premières méthodes, dérivez une classe de la [classe CSettingsStore](../mfc/reference/csettingsstore-class.md) et substituez ses méthodes pour implémenter le chiffrement ou le stockage en dehors du Registre.

- Vous pouvez également désactiver les personnalisations dans votre application.

## <a name="see-also"></a>Voir aussi

[Personnalisation pour MFC](../mfc/customization-for-mfc.md)
