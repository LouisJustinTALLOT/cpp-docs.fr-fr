---
title: Erreur mathématique M6203 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6203
dev_langs:
- C++
helpviewer_keywords:
- M6203
ms.assetid: bd7fdd1c-83e4-4d6a-901e-10a0308bf5be
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d8474c91802b4756207676c466fdd28d66d911b3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022667"
---
# <a name="math-error-m6203"></a>Erreur mathématique M6203

'fonction' : erreur _OVERFLOW

Le résultat de la fonction donnée était trop grand pour être représenté.

Cette erreur appelle le `_matherr` fonction avec le nom de fonction, ses arguments et le type d’erreur. Vous pouvez réécrire la `_matherr` fonction permettant de personnaliser la gestion de certaines erreurs mathématiques à virgule flottante d’exécution.