---
title: Implications en matière de sécurité de personnalisation | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- security, MFC Feature Pack
- MFC Feature Pack, security
ms.assetid: 9be96b12-be38-43bd-a133-5d671265f7a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1416a586af479ea7b476a6c85d45992ba18873ef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379416"
---
# <a name="security-implications-of-customization"></a>Implications en matière de sécurité de la personnalisation
Cette rubrique présente une faille de sécurité potentielle dans MFC.  
  
## <a name="potential-security-weakness"></a>Faille de sécurité potentielle  
 MFC permet à l’utilisateur de personnaliser l’apparence d’une interface utilisateur d’applications, par exemple, l’apparence des boutons et des icônes. MFC prend également en charge les outils définis par l’utilisateur, qui permettent à l’utilisateur d’exécuter des commandes shell. Une faille de sécurité se produit car les paramètres personnalisés de l’application sont enregistrées dans le profil utilisateur dans le Registre. Toute personne qui peut accéder au Registre permettre modifier ces paramètres et modifier l’apparence d’application ou le comportement. Par exemple, un administrateur sur l’ordinateur peut emprunter l’identité utilisateur en forçant l’application de l’utilisateur d’exécuter des programmes arbitraires (même à partir d’un partage réseau).  
  
## <a name="workarounds"></a>Solutions  
 Nous vous recommandons d’une des trois manières de fermer les vulnérabilités dans le Registre :  
  
-   Chiffrer les données qui y sont stockées  
  
-   Stocker les données dans un fichier sécurisé au lieu de dans le Registre.  
  
     Pour effectuer l’une de ces deux premières méthodes, dérivez une classe de [classe CSettingsStore](../mfc/reference/csettingsstore-class.md) et substituer ses méthodes pour implémenter le chiffrement ou le stockage en dehors du Registre.  
  
-   Vous pouvez également désactiver des personnalisations dans votre application.  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation pour MFC](../mfc/customization-for-mfc.md)

