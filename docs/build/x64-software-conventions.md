---
title: Conventions des logiciels x64
ms.date: 12/17/2018
helpviewer_keywords:
- x64 coding conventions
- Visual C++, x64 calling conventions
ms.assetid: 750f3d97-1706-4840-b2fc-41a007329a08
ms.openlocfilehash: 4755cfcf98c9eadbd944e06a56f86ca89a33b0a3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223770"
---
# <a name="x64-software-conventions"></a>Conventions des logiciels x64

Cette section décrit la méthodologie de convention d’appel C++ pour x64, l’extension 64 bits à l’architecture x86.

## <a name="overview-of-x64-calling-conventions"></a>Vue d’ensemble des conventions d’appel x64

Deux différences importantes entre x86 et x64 sont la capacité d’adressage 64 bits et un ensemble plat de registres 16 64 bits pour une utilisation générale. À partir de l’ensemble de registres développé, x64 utilise la Convention d’appel [__fastcall](../cpp/fastcall.md) et un modèle de gestion des exceptions basé sur RISC. La **`__fastcall`** Convention utilise des registres pour les quatre premiers arguments et le frame de pile pour passer des arguments supplémentaires. Pour plus d’informations sur la Convention d’appel x64, y compris l’utilisation des registres, les paramètres de la pile, les valeurs de retour et le déroulement de la pile, consultez [Convention d’appel x64](x64-calling-convention.md).

## <a name="enable-optimization-for-x64"></a>Activer l’optimisation pour x64

L’option de compilateur suivante vous aide à optimiser votre application pour x64 :

- [/favor (optimiser pour les caractéristiques de l’architecture)](../build/reference/favor-optimize-for-architecture-specifics.md)

## <a name="types-and-storage"></a>Types et stockage

Cette section décrit l’énumération et le stockage des types de données pour l’architecture x64.

### <a name="scalar-types"></a>Types scalaires

Bien qu’il soit possible d’accéder aux données avec n’importe quel alignement, il est recommandé d’aligner les données sur leurs limites naturelles ou plusieurs pour éviter la perte de performances. Les enums sont des entiers constants et sont traités comme des entiers 32 bits. Le tableau suivant décrit la définition de type et le stockage recommandé pour les données, car elles se rapportent à l’alignement à l’aide des valeurs d’alignement suivantes :

- Octets-8 bits

- Word-16 bits

- Mot-passe-32 bits

- Mot quadruple-64 bits

- Octaword-128 bits

|||||
|-|-|-|-|
|Type scalaire|Type de données C|Taille de stockage (en octets)|Alignement recommandé|
|**INT8**|**`char`**|1|Byte|
|**DESTINÉES**|**`unsigned char`**|1|Byte|
|**INT16**|**`short`**|2|Word|
|**UINT16**|**`unsigned short`**|2|Word|
|**ENTIER**|**`int`**, **`long`**|4|Mot|
|**UINT32**|**unsigned int, unsigned long**|4|Mot|
|**INT64**|**`__int64`**|8|Mot|
|**UINT64**|**unsigned __int64**|8|Mot|
|**FP32 (simple précision)**|**`float`**|4|Mot|
|**FP64 (double précision)**|**`double`**|8|Mot|
|**DIRIGÉ**|__\*__|8|Mot|
|**`__m64`**|**__m64 de struct**|8|Mot|
|**`__m128`**|**__m128 de struct**|16|Octaword|

### <a name="aggregates-and-unions"></a>Agrégats et unions

D’autres types, tels que des tableaux, des structs et des unions, ont des exigences d’alignement plus strictes qui garantissent une agrégation cohérente et un stockage d’Union et une récupération de données. Voici les définitions du tableau, de la structure et de l’Union :

- Array

   Contient un groupe ordonné d’objets de données adjacents. Chaque objet est appelé un *élément*. Tous les éléments d’un tableau ont la même taille et le même type de données.

- Structure

   Contient un groupe ordonné d’objets de données. Contrairement aux éléments d’un tableau, les objets de données d’une structure peuvent avoir des tailles et des types de données différents. Chaque objet de données dans une structure est appelé *membre*.

- Union

   Objet qui contient l’un des ensembles de membres nommés. Les membres du jeu nommé peuvent être de n’importe quel type. Le stockage alloué pour une Union est égal au stockage requis pour le plus grand membre de cette Union, plus tout remplissage requis pour l’alignement.

Le tableau suivant indique l’alignement fortement suggéré pour les membres scalaires des unions et des structures.

||||
|-|-|-|
|Type scalaire|Type de données C|Alignement requis|
|**INT8**|**`char`**|Byte|
|**DESTINÉES**|**`unsigned char`**|Byte|
|**INT16**|**`short`**|Word|
|**UINT16**|**`unsigned short`**|Word|
|**ENTIER**|**`int`**, **`long`**|Mot|
|**UINT32**|**unsigned int, unsigned long**|Mot|
|**INT64**|**`__int64`**|Mot|
|**UINT64**|**unsigned __int64**|Mot|
|**FP32 (simple précision)**|**`float`**|Mot|
|**FP64 (double précision)**|**`double`**|Mot|
|**DIRIGÉ**|<strong>\*</strong>|Mot|
|**`__m64`**|**__m64 de struct**|Mot|
|**`__m128`**|**__m128 de struct**|Octaword|

Les règles d’alignement d’agrégat suivantes s’appliquent :

- L’alignement d’un tableau est identique à l’alignement de l’un des éléments du tableau.

- L’alignement du début d’une structure ou d’une Union correspond à l’alignement maximal d’un membre individuel. Chaque membre de la structure ou de l’Union doit être placé à son alignement approprié, comme défini dans le tableau précédent, qui peut nécessiter un remplissage interne implicite, en fonction du membre précédent.

- La taille de la structure doit être un multiple entier de son alignement, qui peut nécessiter un remplissage après le dernier membre. Étant donné que les structures et les unions peuvent être regroupées dans des tableaux, chaque élément de tableau d’une structure ou d’une Union doit commencer et se terminer à l’alignement approprié précédemment déterminé.

- Il est possible d’aligner les données de manière à ce qu’elles soient supérieures aux exigences d’alignement tant que les règles précédentes sont conservées.

- Un compilateur individuel peut ajuster la compression d’une structure pour des raisons de taille. Par exemple [,/ZP (Struct Member Alignment)](../build/reference/zp-struct-member-alignment.md) permet d’ajuster la compression des structures.

### <a name="examples-of-structure-alignment"></a>Exemples d'alignement de structure

Les quatre exemples suivants déclarent chacun une structure ou une Union alignée, et les figures correspondantes illustrent la disposition de cette structure ou de cette Union en mémoire. Chaque colonne d’une figure représente un octet de mémoire et le nombre dans la colonne indique le déplacement de cet octet. Le nom de la deuxième ligne de chaque figure correspond au nom d’une variable dans la déclaration. Les colonnes ombrées indiquent un remplissage requis pour atteindre l’alignement spécifié.

#### <a name="example-1"></a>Exemple 1

```C
// Total size = 2 bytes, alignment = 2 bytes (word).

_declspec(align(2)) struct {
    short a;      // +0; size = 2 bytes
}
```

![Présentation de la structure 1 de l’exemple de conversion AMD](../build/media/vcamd_conv_ex_1_block.png "Présentation de la structure 1 de l’exemple de conversion AMD")

#### <a name="example-2"></a>Exemple 2

```C
// Total size = 24 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) struct {
    int a;       // +0; size = 4 bytes
    double b;    // +8; size = 8 bytes
    short c;     // +16; size = 2 bytes
}
```

![Présentation de la structure de l’exemple 2 de conversion AMD](../build/media/vcamd_conv_ex_2_block.png "Présentation de la structure de l’exemple 2 de conversion AMD")

#### <a name="example-3"></a>Exemple 3

```C
// Total size = 12 bytes, alignment = 4 bytes (doubleword).

_declspec(align(4)) struct {
    char a;       // +0; size = 1 byte
    short b;      // +2; size = 2 bytes
    char c;       // +4; size = 1 byte
    int d;        // +8; size = 4 bytes
}
```

![Présentation de la structure de l’exemple 2 de conversion AMD](../build/media/vcamd_conv_ex_3_block.png "Présentation de la structure de l’exemple 2 de conversion AMD")

#### <a name="example-4"></a>Exemple 4

```C
// Total size = 8 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) union {
    char *p;      // +0; size = 8 bytes
    short s;      // +0; size = 2 bytes
    long l;       // +0; size = 4 bytes
}
```

![Exemple de conversion AMD 4 Union layouit](../build/media/vcamd_conv_ex_4_block.png "Exemple de conversion AMD 4 Union layouit")

### <a name="bitfields"></a>Champs de bits

Les champs de bits de structure sont limités à 64 bits et peuvent être de type signed int, unsigned int, Int64 ou unsigned int64. Les champs de bits qui traversent la limite de type ignorent les bits pour aligner le champ de bits à l’alignement de type suivant. Par exemple, les champs de bits entiers ne peuvent pas traverser une limite de 32 bits.

### <a name="conflicts-with-the-x86-compiler"></a>Conflits avec le compilateur x86

Les types de données de plus de 4 octets ne sont pas alignés automatiquement sur la pile lorsque vous utilisez le compilateur x86 pour compiler une application. Étant donné que l’architecture du compilateur x86 est une pile alignée sur 4 octets, toute valeur supérieure à 4 octets, par exemple, un entier 64 bits, ne peut pas être automatiquement alignée sur une adresse de 8 octets.

L’utilisation de données non alignées a deux implications.

- L’accès à des emplacements alignés peut prendre plus de temps que nécessaire.

- Les emplacements non alignés ne peuvent pas être utilisés dans des opérations verrouillées.

Si vous avez besoin d’un alignement plus strict, utilisez `__declspec(align(N))` sur vos déclarations de variable. Cela amène le compilateur à aligner dynamiquement la pile pour répondre à vos spécifications. Toutefois, l’ajustement dynamique de la pile au moment de l’exécution peut ralentir l’exécution de votre application.

## <a name="register-usage"></a>Inscrire l’utilisation

L’architecture x64 fournit pour 16 registres à usage général (ci-après appelés registres d’entiers), ainsi que 16 registres XMM/YMM disponibles pour une utilisation à virgule flottante. Les registres volatils sont des registres de travail censés être détruits après un appel. Les registres non volatils doivent conserver leurs valeurs tout au long d'un appel de fonction et être enregistrés par l'appelé s'il les utilise.

### <a name="register-volatility-and-preservation"></a>Inscrire la volatilité et la préservation

Le tableau suivant explique comment chaque registre est utilisé dans les appels de fonction :

||||
|-|-|-|
|Inscrire|Statut|Utilisation|
|RAX|Volatil|Registre des valeurs de retour|
|RCX|Volatil|Premier argument entier|
|RDX|Volatil|Deuxième argument entier|
|R8|Volatil|Troisième argument entier|
|R9|Volatil|Quatrième argument entier|
|R10:R11|Volatil|Doit être conservé si nécessaire par l'appelant ; utilisé dans les instructions syscall/sysret|
|R12:R15|Non volatil|Doit être conservé par l'appelé|
|RDI|Non volatil|Doit être conservé par l'appelé|
|RSI|Non volatil|Doit être conservé par l'appelé|
|RBX|Non volatil|Doit être conservé par l'appelé|
|RBP|Non volatil|Peut être utilisé comme pointeur de frame ; doit être conservé par l'appelé|
|RSP|Non volatil|Pointeur de pile|
|XMM0, YMM0|Volatil|Premier argument FP ; premier argument de type vectoriel quand **`__vectorcall`** est utilisé|
|XMM1, YMM1|Volatil|Deuxième argument FP ; deuxième argument de type vectoriel quand **`__vectorcall`** est utilisé|
|XMM2, YMM2|Volatil|Troisième argument FP ; troisième argument de type vectoriel quand **`__vectorcall`** est utilisé|
|XMM3, YMM3|Volatil|Quatrième argument FP ; quatrième argument de type vectoriel quand **`__vectorcall`** est utilisé|
|XMM4, YMM4|Volatil|Doit être conservé si nécessaire par l’appelant ; cinquième argument de type vectoriel quand **`__vectorcall`** est utilisé|
|XMM5, YMM5|Volatil|Doit être conservé si nécessaire par l’appelant ; sixième argument de type vectoriel quand **`__vectorcall`** est utilisé|
|XMM6:XMM15, YMM6:YMM15|Non volatil (XMM), volatil (moitié supérieure de YMM)|Doit être conservé par l’appelé. Les registres YMM doivent être conservés si nécessaire par l'appelant.|

Sur la sortie de la fonction et sur l’entrée de la fonction pour les appels de la bibliothèque Runtime C et les appels système Windows, l’indicateur de direction dans le registre des indicateurs de l’UC est supposé être effacé.

## <a name="stack-usage"></a>Utilisation de la pile

Pour plus d’informations sur l’allocation de pile, l’alignement, les types de fonction et les frames de pile sur x64, consultez Utilisation de la [pile x64](stack-usage.md).

## <a name="prolog-and-epilog"></a>Prologue et épilogue

Chaque fonction qui alloue de l’espace de pile, appelle d’autres fonctions, enregistre les registres non volatiles ou utilise la gestion des exceptions doit avoir un prologue dont les limites d’adresse sont décrites dans les données de déroulement associées à l’entrée de table de fonctions respective et épilogues à chaque sortie d’une fonction. Pour plus d’informations sur le prologue et le code d’épilogue requis sur x64, consultez [prologue et épilogue x64](prolog-and-epilog.md).

## <a name="x64-exception-handling"></a>Gestion d’exceptions x64

Pour plus d’informations sur les conventions et les structures de données utilisées pour implémenter la gestion structurée des exceptions et le comportement de gestion des exceptions C++ sur le x64, consultez [gestion des exceptions x64](exception-handling-x64.md).

## <a name="intrinsics-and-inline-assembly"></a>Assembly intrinsèques et Inline

L’une des contraintes pour le compilateur x64 est l’absence de prise en charge de l’assembleur inline. Cela signifie que les fonctions qui ne peuvent pas être écrites en C ou C++ devront être écrites en tant que sous-routines ou en tant que fonctions intrinsèques prises en charge par le compilateur. Certaines fonctions sont sensibles aux performances, tandis que d’autres ne le sont pas. Les fonctions sensibles aux performances doivent être implémentées en tant que fonctions intrinsèques.

Les intrinsèques pris en charge par le compilateur sont décrits dans [intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md).

## <a name="image-format"></a>Format d’image

Le format d’image exécutable x64 est PE32 +. Les images exécutables (dll et exe) sont limitées à une taille maximale de 2 gigaoctets, de sorte que l’adressage relatif avec un déplacement 32 bits peut être utilisé pour traiter les données d’image statique. Ces données incluent la table d’adresses d’importation, les constantes de chaîne, les données globales statiques, etc.

## <a name="see-also"></a>Voir aussi

[Conventions d’appel](../cpp/calling-conventions.md)
