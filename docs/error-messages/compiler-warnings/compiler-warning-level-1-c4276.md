---
title: Compilateur avertissement (niveau 1) C4276 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4276
dev_langs:
- C++
helpviewer_keywords:
- C4276
ms.assetid: 9d738c2d-29e5-408a-b9ff-be1a850b2238
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 40a6c85b460e9718a8816598afb016e9c7a493b9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116020"
---
# <a name="compiler-warning-level-1-c4276"></a>Avertissement du compilateur (niveau 1) C4276

'fonction' : aucun prototype fourni ; supposé sans paramètres

Lorsque vous prenez l’adresse d’une fonction avec la [__stdcall](../../cpp/stdcall.md) convention d’appel, vous devez donner un prototype afin que le compilateur peut créer le nom décoré de la fonction. Dans la mesure où *fonction* a pas de prototype, le compilateur, lors de la création du nom décoré, suppose que la fonction n’a aucun paramètre.