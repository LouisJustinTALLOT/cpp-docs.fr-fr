---
description: 'En savoir plus sur : erreur du compilateur C2097'
title: Erreur du compilateur C2097
ms.date: 11/04/2016
f1_keywords:
- C2097
helpviewer_keywords:
- C2097
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
ms.openlocfilehash: b9aa67f85ce9ba60a693500a2d7e3f69014cbba3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97278608"
---
# <a name="compiler-error-c2097"></a>Erreur du compilateur C2097

initialisation non conforme

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Initialisation d’une variable à l’aide d’une valeur non constante.

1. Initialisation d’une adresse de petite taille avec une adresse longue.

1. Initialisation d’une structure, d’une Union ou d’un tableau local avec une expression non constante lors de la compilation avec **/za**.

1. Initialisation avec une expression contenant un opérateur virgule.

1. Initialisation avec une expression qui n’est ni constante ni symbolique.
