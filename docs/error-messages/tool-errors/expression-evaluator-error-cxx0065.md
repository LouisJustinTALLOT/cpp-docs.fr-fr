---
title: Évaluateur d'expression, erreur CXX0065
ms.date: 11/04/2016
f1_keywords:
- CXX0065
helpviewer_keywords:
- CAN0065
- CXX0065
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
ms.openlocfilehash: b4120deec3c8e7ce14e381f782904cf83a588e43
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80184422"
---
# <a name="expression-evaluator-error-cxx0065"></a>Évaluateur d'expression, erreur CXX0065

la variable a besoin d’un frame de pile

Une expression contient une variable qui existe dans l’étendue actuelle, mais n’a pas encore été créée.

Cette erreur peut se produire lorsque vous avez effectué un pas à pas détaillé dans le prologue d’une fonction, mais que vous n’avez pas encore configuré le frame de pile pour la fonction, ou si vous avez effectué un pas à pas détaillé dans le code de sortie de la fonction.

Parcourez le code de prologue jusqu’à ce que le frame de pile ait été configuré avant d’évaluer l’expression.

Cette erreur est identique à CAN0065.
