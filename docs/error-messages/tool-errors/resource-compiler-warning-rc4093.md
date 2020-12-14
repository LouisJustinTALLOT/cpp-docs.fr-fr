---
description: 'En savoir plus sur : avertissement du compilateur de ressources RC4093'
title: 'Avertissement RC4093 du compilateur de ressources '
ms.date: 11/04/2016
f1_keywords:
- RC4093
helpviewer_keywords:
- RC4093
ms.assetid: 3c61b4a4-b418-465b-a4fd-cb1ff0adb8dd
ms.openlocfilehash: 40f4777bb62fc2a5e434a4a365cdd027a04ffafd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97237086"
---
# <a name="resource-compiler-warning-rc4093"></a>Avertissement RC4093 du compilateur de ressources 

saut de ligne sans séquence d’échappement dans une constante caractère dans du code inactif

L’expression constante d’une `#if` `#elif` directive de préprocesseur,, **#ifdef** ou **#ifndef** a été évaluée à zéro, ce qui rend le code qui suit inactif. Dans ce code inactif, un caractère de saut de ligne apparaissait dans un jeu de guillemets simples ou doubles.

Tout le texte jusqu’à ce que le guillemet double suivant soit considéré comme se trouvant dans une constante caractère.
