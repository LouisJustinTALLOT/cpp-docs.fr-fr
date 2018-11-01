---
title: Erreur des outils Éditeur de liens LNK2004
ms.date: 11/04/2016
f1_keywords:
- LNK2004
helpviewer_keywords:
- LNK2004
ms.assetid: 07645371-e67b-4a2c-b0e0-dde24c94ef7e
ms.openlocfilehash: 37eb01b5dd8266bce34e1a932271d5d9a9d15c52
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50529322"
---
# <a name="linker-tools-error-lnk2004"></a>Erreur des outils Éditeur de liens LNK2004

dépassement de la correction relative GP à 'target' ; la section short 'section' est trop grande ou hors limites.

La section était trop grande.

Pour résoudre cette erreur, réduisez la taille de la section short, soit en insérant explicitement des données dans les sections long via #pragma section (« .sectionname », lecture, écriture, long) à l’aide de `__declspec(allocate(".sectionname"))` sur les déclarations et définitions de données.  Par exemple :

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

Vous pouvez également déplacer les données regroupées logiquement dans leur propre structure qui sera une collection de données supérieures à 8 octets, allouée dans une section de données de type long le compilateur.  Par exemple :

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

Cette erreur est suivie d’une erreur irrécupérable `LNK1165`.