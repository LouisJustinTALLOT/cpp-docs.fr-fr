---
title: Erreur irrécupérable C1013 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1013
dev_langs:
- C++
helpviewer_keywords:
- C1013
ms.assetid: 5514a679-efe7-4055-bdd3-5693ca0c332f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33c10062cac83984fb1c68835780497b89c4cbc1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050509"
---
# <a name="fatal-error-c1013"></a>Erreur irrécupérable C1013

limite du compilateur : parenthèses ouvertes trop nombreuses

Une expression contient trop de niveaux de parenthèses pour une même expression. Simplifiez l’expression ou scindez-la en plusieurs instructions.

Avant Visual C++ 6.0 Service Pack 3, la limite d’imbrication de parenthèses dans une même expression était de 59. Actuellement, cette limite est de 256.