---
title: Avertissement RC4093 du compilateur de ressources
ms.date: 11/04/2016
f1_keywords:
- RC4093
helpviewer_keywords:
- RC4093
ms.assetid: 3c61b4a4-b418-465b-a4fd-cb1ff0adb8dd
ms.openlocfilehash: 29d24f1e380f5c531e170e5dc23cf5c77eefb874
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182290"
---
# <a name="resource-compiler-warning-rc4093"></a>Avertissement RC4093 du compilateur de ressources

saut de ligne sans séquence d’échappement dans une constante caractère dans du code inactif

L’expression constante d’une directive de préprocesseur `#if`, `#elif`, **#ifdef**ou **#ifndef** a été évaluée à zéro, ce qui rend le code qui suit inactif. Dans ce code inactif, un caractère de saut de ligne apparaissait dans un jeu de guillemets simples ou doubles.

Tout le texte jusqu’à ce que le guillemet double suivant soit considéré comme se trouvant dans une constante caractère.
