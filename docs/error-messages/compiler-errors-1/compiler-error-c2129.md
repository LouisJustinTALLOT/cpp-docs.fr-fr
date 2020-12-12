---
description: 'En savoir plus sur : erreur du compilateur C2129'
title: Erreur du compilateur C2129
ms.date: 11/04/2016
f1_keywords:
- C2129
helpviewer_keywords:
- C2129
ms.assetid: 21a8223e-1d22-4baa-9ca1-922b7f751dd0
ms.openlocfilehash: 5efb19aa3f4edd14dd6cfab93c3880745b08e59d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323153"
---
# <a name="compiler-error-c2129"></a>Erreur du compilateur C2129

fonction static’Function’déclarée mais non définie

Une référence anticipée est apportée à une **`static`** fonction qui n’est jamais définie.

Une **`static`** fonction doit être définie dans la portée du fichier. Si la fonction est définie dans un autre fichier, elle doit être déclarée **`extern`** .
