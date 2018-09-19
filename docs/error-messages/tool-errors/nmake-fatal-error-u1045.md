---
title: Erreur irrécupérable NMAKE U1045 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1045
dev_langs:
- C++
helpviewer_keywords:
- U1045
ms.assetid: dc70d162-14b9-4107-9237-7514044d72e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2b9be4f7440d9e79d603e917c1886aebe7c44af
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056883"
---
# <a name="nmake-fatal-error-u1045"></a>Erreur irrécupérable NMAKE U1045

échec de la génération dynamique : message

Un programme ou une commande appelé par NMAKE a échoué pour la raison indiquée. Quand NMAKE appelle un autre programme (par exemple, le compilateur ou l'éditeur de liens), l'appel peut échouer ou une erreur peut être retournée par le programme appelé. Ce message est utilisé pour signaler l'erreur.

Pour résoudre ce problème, commencez par déterminer la cause de l'erreur. Vous pouvez utiliser les commandes indiquées par le NMAKE [/N](../../build/nmake-options.md) option pour vérifier les paramètres d’environnement et répéter les actions effectuées par NMAKE sur la ligne de commande.