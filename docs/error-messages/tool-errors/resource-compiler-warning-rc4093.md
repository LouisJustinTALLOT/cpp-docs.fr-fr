---
title: Avertissement RC4093 du compilateur de ressources | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC4093
dev_langs:
- C++
helpviewer_keywords:
- RC4093
ms.assetid: 3c61b4a4-b418-465b-a4fd-cb1ff0adb8dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9b1ca04b17ebdb9d48bc94032482caf48ad4aa00
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111561"
---
# <a name="resource-compiler-warning-rc4093"></a>Avertissement RC4093 du compilateur de ressources 

saut de ligne sans séquence d’échappement dans une constante caractère du code inactif

L’expression constante d’un `#if`, `#elif`, **#ifdef**, ou **#ifndef** directive de préprocesseur à zéro, ce qui rend le code qui suit inactif. Dans ce code inactif, un caractère de saut de ligne apparaît dans un jeu de guillemets simples ou doubles.

Tout le texte jusqu'à ce que le guillemet suivant a été considéré comme dans une constante caractère.