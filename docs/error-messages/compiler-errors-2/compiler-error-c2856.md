---
title: Erreur du compilateur C2856
ms.date: 11/04/2016
f1_keywords:
- C2856
helpviewer_keywords:
- C2856
ms.assetid: fe616c51-124e-49e3-9dd8-883ec1660680
ms.openlocfilehash: 1e515f250c8ab9d1008ded91b99176f1d86d7cd1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499604"
---
# <a name="compiler-error-c2856"></a>Erreur du compilateur C2856

\#pragma hdrstop ne peut pas être dans un bloc #if

Le `hdrstop` pragma ne peut pas être placé dans le corps d’un bloc de compilation conditionnelle.

Déplacer le `#pragma hdrstop` instruction vers une zone qui n’est pas contenue dans un `#if/#endif` bloc.