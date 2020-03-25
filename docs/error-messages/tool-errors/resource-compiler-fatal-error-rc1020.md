---
title: Erreur irrécupérable RC1020 du compilateur de ressources
ms.date: 11/04/2016
f1_keywords:
- RC1020
helpviewer_keywords:
- RC1020
ms.assetid: 3e073ebf-9136-4bf8-ac6a-3c642ed64594
ms.openlocfilehash: ff4cc5564f59d0adf74ae86149130dd5d017a9ae
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182680"
---
# <a name="resource-compiler-fatal-error-rc1020"></a>Erreur irrécupérable RC1020 du compilateur de ressources

' #endif’inattendu

Une directive de `#endif` est apparue sans directive de `#if`, **#ifdef**ou **#ifndef** correspondante.

Assurez-vous qu’il existe une `#endif` correspondante pour chaque instruction `#if`, **#ifdef**et **#ifndef** .
