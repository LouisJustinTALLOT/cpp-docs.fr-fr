---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4276'
title: Avertissement du compilateur (niveau 1) C4276
ms.date: 11/04/2016
f1_keywords:
- C4276
helpviewer_keywords:
- C4276
ms.assetid: 9d738c2d-29e5-408a-b9ff-be1a850b2238
ms.openlocfilehash: 14b13b2eb1e13d28f2b208e52ef71e1c729fe5e0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97311784"
---
# <a name="compiler-warning-level-1-c4276"></a>Avertissement du compilateur (niveau 1) C4276

'fonction' : aucun prototype fourni ; aucun paramètre pris par défaut

Lorsque vous prenez l’adresse d’une fonction avec la Convention d’appel [__stdcall](../../cpp/stdcall.md) , vous devez attribuer un prototype afin que le compilateur puisse créer le nom décoré de la fonction. Étant donné que la *fonction* n’a pas de prototype, le compilateur, lors de la création du nom décoré, suppose que la fonction n’a aucun paramètre.
