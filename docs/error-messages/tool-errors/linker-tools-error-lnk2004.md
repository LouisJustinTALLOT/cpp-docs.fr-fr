---
description: 'En savoir plus sur : erreur des outils Éditeur de liens LNK2004'
title: Erreur des outils Éditeur de liens LNK2004
ms.date: 11/04/2016
f1_keywords:
- LNK2004
helpviewer_keywords:
- LNK2004
ms.assetid: 07645371-e67b-4a2c-b0e0-dde24c94ef7e
ms.openlocfilehash: 6fc08f343726e6b037c33e9eef53d3fbac8f176f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338516"
---
# <a name="linker-tools-error-lnk2004"></a>Erreur des outils Éditeur de liens LNK2004

dépassement de la correction GP relative à’target'; la section Short’section’est trop grande ou hors limites.

La section était trop grande.

Pour résoudre cette erreur, réduisez la taille de la section, en plaçant les données de manière explicite dans les sections longues via #pragma section (« ., », lire, écrire, long) et en utilisant `__declspec(allocate(".sectionname"))` sur les définitions et les déclarations de données.  Par exemple :

```
#pragma section(".data$mylong", read, write, long)
__declspec(allocate(".data$mylong"))
char    rg0[1] = { 1 };
char    rg1[2] = { 1 };
char    rg2[4] = { 1 };
char    rg3[8] = { 1 };
char    rg4[16] = { 1 };
char    rg5[32] = { 1 };
```

Vous pouvez également déplacer des données groupées logiquement dans sa propre structure qui sera une collection de données supérieure à 8 octets, que le compilateur allouera dans une section de données de type long.  Par exemple :

```
// from this...
int     w1  = 23;
int     w2 = 46;
int     w3 = 23*3;
int     w4 = 23*4;

// to this...
struct X {
    int     w1;
    int     w2;
    int     w3;
    int     w4;
} x  = { 23, 23*2, 23*3, 23*4 };
```

Cette erreur est suivie d’une erreur irrécupérable `LNK1165` .
