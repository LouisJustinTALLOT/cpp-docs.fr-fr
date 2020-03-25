---
title: Erreur du compilateur C2856
ms.date: 11/04/2016
f1_keywords:
- C2856
helpviewer_keywords:
- C2856
ms.assetid: fe616c51-124e-49e3-9dd8-883ec1660680
ms.openlocfilehash: c88610607083ecfaf5f20cd585b479991fa51b44
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201875"
---
# <a name="compiler-error-c2856"></a>Erreur du compilateur C2856

\#pragma hdrstop ne peut pas se trouver à l’intérieur d’un bloc #if

Le pragma `hdrstop` ne peut pas être placé dans le corps d’un bloc de compilation conditionnelle.

Déplacez l’instruction `#pragma hdrstop` dans une zone qui n’est pas contenue dans un bloc `#if/#endif`.
