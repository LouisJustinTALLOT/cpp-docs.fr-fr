---
description: 'En savoir plus sur : erreur du compilateur C3550'
title: Erreur du compilateur C3550
ms.date: 11/04/2016
f1_keywords:
- C3550
helpviewer_keywords:
- C3550
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
ms.openlocfilehash: 4cb459e3f8e7fdd0dbb00c1d4dfaa3c3c6b1eb71
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97112412"
---
# <a name="compiler-error-c3550"></a>Erreur du compilateur C3550

'decltype(auto)' simple est le seul autorisé dans ce contexte

Si `decltype(auto)` est utilisé comme espace réservé pour le type de retour d'une fonction, il doit être utilisé par lui-même. Il ne peut pas être utilisé dans le cadre d'une déclaration de pointeur (`decltype(auto*)`), d'une déclaration de référence (`decltype(auto&)`) ni de toute autre qualification de ce genre.

## <a name="see-also"></a>Voir aussi

[Auto](../../cpp/auto-cpp.md)
