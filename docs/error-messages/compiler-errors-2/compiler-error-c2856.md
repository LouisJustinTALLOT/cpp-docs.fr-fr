---
title: Erreur du compilateur C2856 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2856
dev_langs:
- C++
helpviewer_keywords:
- C2856
ms.assetid: fe616c51-124e-49e3-9dd8-883ec1660680
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: df6226bfd2fc11f05f894091f4ff02c145d09e11
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072710"
---
# <a name="compiler-error-c2856"></a>Erreur du compilateur C2856

\#pragma hdrstop ne peut pas être dans un bloc #if

Le `hdrstop` pragma ne peut pas être placé dans le corps d’un bloc de compilation conditionnelle.

Déplacer le `#pragma hdrstop` instruction vers une zone qui n’est pas contenue dans un `#if/#endif` bloc.