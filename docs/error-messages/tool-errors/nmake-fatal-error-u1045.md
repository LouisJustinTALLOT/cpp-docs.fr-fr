---
title: Erreur irrécupérable NMAKE U1045
ms.date: 11/04/2016
f1_keywords:
- U1045
helpviewer_keywords:
- U1045
ms.assetid: dc70d162-14b9-4107-9237-7514044d72e3
ms.openlocfilehash: 0937e83303fefdf1f2aaaa5eea6f43c27159fd57
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344392"
---
# <a name="nmake-fatal-error-u1045"></a>Erreur irrécupérable NMAKE U1045

échec de la génération dynamique : message

Un programme ou une commande appelé par NMAKE a échoué pour la raison indiquée. Quand NMAKE appelle un autre programme (par exemple, le compilateur ou l'éditeur de liens), l'appel peut échouer ou une erreur peut être retournée par le programme appelé. Ce message est utilisé pour signaler l'erreur.

Pour résoudre ce problème, commencez par déterminer la cause de l'erreur. Vous pouvez utiliser les commandes indiquées par le NMAKE [/N](../../build/reference/nmake-options.md) option pour vérifier les paramètres d’environnement et répéter les actions effectuées par NMAKE sur la ligne de commande.