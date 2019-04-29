---
title: 'Avertissement RC4093 du compilateur de ressources '
ms.date: 11/04/2016
f1_keywords:
- RC4093
helpviewer_keywords:
- RC4093
ms.assetid: 3c61b4a4-b418-465b-a4fd-cb1ff0adb8dd
ms.openlocfilehash: 23bf436e6e8338f89bc576564181c84715028332
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346208"
---
# <a name="resource-compiler-warning-rc4093"></a>Avertissement RC4093 du compilateur de ressources 

saut de ligne sans séquence d’échappement dans une constante caractère du code inactif

L’expression constante d’un `#if`, `#elif`, **#ifdef**, ou **#ifndef** directive de préprocesseur à zéro, ce qui rend le code qui suit inactif. Dans ce code inactif, un caractère de saut de ligne apparaît dans un jeu de guillemets simples ou doubles.

Tout le texte jusqu'à ce que le guillemet suivant a été considéré comme dans une constante caractère.