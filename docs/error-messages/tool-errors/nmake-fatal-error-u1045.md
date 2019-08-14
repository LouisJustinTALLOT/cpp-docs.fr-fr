---
title: Erreur irrécupérable NMAKE U1045
ms.date: 08/11/2019
f1_keywords:
- U1045
helpviewer_keywords:
- U1045
ms.assetid: dc70d162-14b9-4107-9237-7514044d72e3
ms.openlocfilehash: bdc28bcf02aea791a346a0a74915707fef551b8b
ms.sourcegitcommit: db1ed91fa7451ade91c3fb76bc7a2b857f8a5eef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68980542"
---
# <a name="nmake-fatal-error-u1045"></a>Erreur irrécupérable NMAKE U1045

> échec de la génération dynamique: *message*

Un programme ou une commande appelé par NMAKE a échoué pour la raison dans le *message*. Lorsque NMAKE appelle un autre programme, par exemple, le compilateur ou l’éditeur de liens, l’appel peut échouer. Ou une erreur peut être retournée par le programme appelé. Ce message est utilisé pour signaler l'erreur.

Pour résoudre ce problème, commencez par déterminer la cause de l'erreur. Vous pouvez utiliser les commandes indiquées par l’option NMAKE [/n](../../build/reference/running-nmake.md#nmake-options) pour vérifier les paramètres d’environnement et répéter les actions effectuées par NMAKE sur la ligne de commande.
