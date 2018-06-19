---
title: LNK2004 d’erreur des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2004
dev_langs:
- C++
helpviewer_keywords:
- LNK2004
ms.assetid: 07645371-e67b-4a2c-b0e0-dde24c94ef7e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2619ebc3fcf997574628354a951619cd18a81b46
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33314338"
---
# <a name="linker-tools-error-lnk2004"></a>Erreur des outils Éditeur de liens LNK2004
dépassement de la correction relative GP à 'cible' ; la section short 'section' est trop grande ou hors limites.  
  
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
  
 Vous pouvez également déplacer des données groupées logiquement dans leur propre structure qui sera une collection de données supérieure à 8 octets, allouée par le compilateur dans une section de données de type long.  Par exemple :  
  
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