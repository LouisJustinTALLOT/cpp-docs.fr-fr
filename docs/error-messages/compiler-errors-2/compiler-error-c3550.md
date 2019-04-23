---
title: Erreur du compilateur C3550
ms.date: 11/04/2016
f1_keywords:
- C3550
helpviewer_keywords:
- C3550
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
ms.openlocfilehash: 106ac93496eebb25ee603251d84680053e1310b7
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59032334"
---
# <a name="compiler-error-c3550"></a>Erreur du compilateur C3550

'decltype(auto)' simple est le seul autorisé dans ce contexte

Si `decltype(auto)` est utilisé comme espace réservé pour le type de retour d'une fonction, il doit être utilisé par lui-même. Il ne peut pas être utilisé dans le cadre d'une déclaration de pointeur (`decltype(auto*)`), d'une déclaration de référence (`decltype(auto&)`) ni de toute autre qualification de ce genre.

## <a name="see-also"></a>Voir aussi

[auto](../../cpp/auto-cpp.md)