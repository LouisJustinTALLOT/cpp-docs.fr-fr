---
title: Opérateurs de bits C
ms.date: 01/29/2018
helpviewer_keywords:
- '| operator, bitwise operators'
- bitwise operators, Visual C
- bitwise operators
- operators [C], bitwise
- ^ operator, bitwise operators
- AND operator
- ampersand operator (&)
- ^ operator
- '& operator, bitwise operators'
ms.assetid: e22127b1-9a2d-4876-b01d-c8f72cec3317
ms.openlocfilehash: 50be8ae38f21d0a9f46c180abf179e1358b707cd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168771"
---
# <a name="c-bitwise-operators"></a>Opérateurs de bits C

Les opérateurs au niveau du bit effectuent de bits AND ( **&** ), des opérations de bits OR exclusives ( **^** ) et opérations de bits OR inclusives ( **&#124;** ).

## <a name="syntax"></a>Syntaxe

*And-expression*: &nbsp;&nbsp;*expression d’égalité* &nbsp;&nbsp;*et-expression* **&** *égalité-* expression

*exclusive-or-expression*: &nbsp;&nbsp;*et-expression* &nbsp;&nbsp;*exclusive-OR-expression* **^** *et-* expression exclusive

*inclusif-or-expression*: &nbsp;&nbsp;&nbsp;*exclusif* ou à une expression &nbsp;*inclusive* &#124; *-or* -expression

Les opérandes des opérateurs de bits doivent avoir des types intégraux, mais leurs types peuvent être différents. Ces opérateurs exécutent les conversions arithmétiques habituelles ; le type du résultat est le type de l'opérande après conversion.

Les opérateurs de bits C sont décrits ci-dessous :

|Opérateur|Description|
|--------------|-----------------|
|**&**|L'opérateur de bits AND compare chaque bit de son premier opérande au bit correspondant de son second opérande. Si les deux bits ont pour valeur 1, le bit obtenu correspondant a pour valeur 1. Sinon, il a pour valeur 0.|
|**^**|L’opérateur de bits OR exclusif compare chaque bit de son premier opérande au bit correspondant de son second opérande. Si un bit a pour valeur 0 et que l'autre a pour valeur 1, le bit obtenu correspondant a pour valeur 1. Sinon, il a pour valeur 0.|
|**&#124;**|L’opérateur de bits OR exclusif compare chaque bit de son premier opérande au bit correspondant de son second opérande. Si l'un des deux bits a pour valeur 1, le bit obtenu correspondant a pour valeur 1. Sinon, il a pour valeur 0.|

## <a name="examples"></a>Exemples

Ces déclarations sont utilisées pour les trois exemples suivants :

```C
short i = 0xAB00;
short j = 0xABCD;
short n;

n = i & j;
```

Le résultat affecté à `n` dans ce premier exemple est le même que `i` (0xAB00 hexadécimal).

```C
n = i | j;

n = i ^ j;
```

L’OR inclusif au niveau du bit dans le deuxième exemple entraîne la valeur 0xABCD (hexadécimale), tandis que l’opération OR exclusive au niveau du bit dans le troisième exemple produit 0xCD (hexadécimal).

**Section spécifique de Microsoft**

Les résultats d’une opération au niveau du bit sur des entiers signés sont définis par l’implémentation en fonction de la norme ANSI C. Pour le compilateur Microsoft C, les opérations au niveau du bit sur les entiers signés fonctionnent de la même façon que les opérations au niveau du bit sur les entiers non signés. Par exemple, les valeurs `-16 & 99` peuvent être exprimées au format binaire sous la forme

```Expression
  11111111 11110000
& 00000000 01100011
  _________________
  00000000 01100000
```

Le résultat de l'opération de bits AND est 96 décimal.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[Opérateur de bits AND : &](../cpp/bitwise-and-operator-amp.md)<br/>
[Opérateur de bits OR exclusif : ^](../cpp/bitwise-exclusive-or-operator-hat.md)<br/>
[Opérateur de bits OR inclusif : &#124;](../cpp/bitwise-inclusive-or-operator-pipe.md)
