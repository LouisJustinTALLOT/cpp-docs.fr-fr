---
title: x64 conventions des logiciels
ms.date: 12/17/2018
helpviewer_keywords:
- x64 coding conventions
- Visual C++, x64 calling conventions
ms.assetid: 750f3d97-1706-4840-b2fc-41a007329a08
ms.openlocfilehash: 11d29b6c31ccecfe5b9c51c2f9311213bd4a6732
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57420269"
---
# <a name="x64-software-conventions"></a>x64 conventions des logiciels

Cette section décrit la méthodologie de convention d’appel pour x64, l’extension de 64 bits pour le x86 C++ architecture.

## <a name="overview-of-x64-calling-conventions"></a>Vue d’ensemble des conventions d’appel de x64

Deux différences importantes entre x86 et x64 sont la fonction d’adressage 64 bits et un jeu de 16 bits 64 registres pour une utilisation générale. Étant donné le jeu de Registre développé, l’utilise x64 le [__fastcall](../cpp/fastcall.md) convention d’appel et un modèle de gestion des exceptions basé sur RISC. Le `__fastcall` convention utilise des registres pour les quatre premiers arguments et le frame de pile pour passer des arguments supplémentaires. Pour plus d’informations sur la x64 convention d’appel, y compris l’utilisation des registres, les paramètres de pile, retourner les valeurs et le déroulement de pile, consultez [x64 convention d’appel](x64-calling-convention.md).

## <a name="enable-optimization-for-x64"></a>Activer l’optimisation pour x64

L’option du compilateur suivante vous aide à optimiser votre application pour x64 :

- [/favor (Optimisation pour les particularités d’architecture)](../build/reference/favor-optimize-for-architecture-specifics.md)

## <a name="types-and-storage"></a>Types et stockage

Cette section décrit l’énumération et le stockage des types de données pour le x64 architecture.

### <a name="scalar-types"></a>types scalaires

Bien qu’il soit possible d’accéder aux données avec un alignement quelconque, il est recommandé d’aligner les données à sa limite naturelle ou certains multiple, pour éviter la perte de performances. Les enums sont des entiers constants et sont traités comme des entiers 32 bits. Le tableau suivant décrit la définition de type et le stockage recommandé pour les données relative à l’alignement en utilisant les valeurs d’alignement suivantes :

- Byte - 8 bits

- Word - 16 bits

- Mot double - 32 bits

- Mot quadruple - 64 bits

- Octaword - 128 bits

|||||
|-|-|-|-|
|Type scalaire|Type de données C|Taille de stockage (en octets)|Alignement recommandé|
|**INT8**|**char**|1|Byte|
|**UINT8**|**unsigned char**|1|Byte|
|**INT16**|**short**|2|Word|
|**UINT16**|**unsigned short**|2|Word|
|**INT32**|**int**, **long**|4|Doubleword|
|**UINT32**|**unsigned int, unsigned long**|4|Doubleword|
|**INT64**|**__int64**|8|Quadword|
|**UINT64**|**unsigned __int64**|8|Quadword|
|**FP32 (simple précision)**|**float**|4|Doubleword|
|**FP64 (double précision)**|**double**|8|Quadword|
|**POINTEUR**|__\*__|8|Quadword|
|**__m64**|**struct __m64**|8|Quadword|
|**__m128**|**struct __m128**|16|Octaword|

### <a name="aggregates-and-unions"></a>Agrégats et unions

Autres types, tels que des tableaux, des structs et unions, ont des exigences plus strictes de l’alignement qui garantissent la cohérence agrégée et union stockage et extraction des données. Voici les définitions de tableau, de structure et d’union :

- Tableau

   Contient un groupe ordonné d’objets de données adjacents. Chaque objet est appelé un *élément*. Tous les éléments dans un tableau ont la même taille et type de données.

- Structure

   Contient un groupe ordonné d’objets de données. Contrairement aux éléments d’un tableau, les objets de données au sein d’une structure peuvent avoir des tailles et types de données différents. Chaque objet de données dans une structure est appelé un *membre*.

- Union

   Objet qui contient l’un d’un jeu de membres nommés. Les membres du jeu nommé peuvent être de n’importe quel type. Le stockage alloué pour une union est égal au stockage requis pour le plus grand membre de cette union, plus tout remplissage requis pour l’alignement.

Le tableau suivant présente l’alignement vivement recommandé pour les membres scalaires des unions et des structures.

||||
|-|-|-|
|Type scalaire|Type de données C|Alignement requis|
|**INT8**|**char**|Byte|
|**UINT8**|**unsigned char**|Byte|
|**INT16**|**short**|Word|
|**UINT16**|**unsigned short**|Word|
|**INT32**|**int**, **long**|Doubleword|
|**UINT32**|**unsigned int, unsigned long**|Doubleword|
|**INT64**|**__int64**|Quadword|
|**UINT64**|**unsigned __int64**|Quadword|
|**FP32 (simple précision)**|**float**|Doubleword|
|**FP64 (double précision)**|**double**|Quadword|
|**POINTEUR**|<strong>\*</strong>|Quadword|
|**__m64**|**struct __m64**|Quadword|
|**__m128**|**struct __m128**|Octaword|

Les règles d’alignement d’agrégation suivantes s’appliquent :

- L’alignement d’un tableau est le même que l’alignement d’un des éléments du tableau.

- L’alignement du début d’une structure ou une union est l’alignement maximale de tous les membres individuels. Chaque membre au sein de la structure ou union doit être placé à son propre alignement comme défini dans le tableau précédent, ce qui peut nécessiter un remplissage interne implicite selon le membre précédent.

- Taille de la structure doit être un multiple entier de son alignement, laquelle peut requérir une marge intérieure après le dernier membre. Dans la mesure où les structures et les unions peuvent être regroupées dans des tableaux, chaque élément du tableau d’une structure ou une union doit commencer et se terminer à l’alignement correct préalablement déterminée.

- Il est possible d’aligner les données de manière à être supérieure à la configuration requise d’alignement, que les règles précédentes sont conservées.

- Un compilateur individuel peut ajuster la compression d’une structure pour des raisons de taille. Par exemple [/Zp (alignement des membres de Struct)](../build/reference/zp-struct-member-alignment.md) permet d’ajuster l’emballage de structures.

### <a name="examples-of-structure-alignment"></a>Exemples d'alignement de structure

Les quatre exemples ci-dessous chaque déclarent qu'une aligné structure ou union et les chiffres correspondantes illustrent la disposition de cette structure ou union en mémoire. Chaque colonne dans une illustration représente un octet de mémoire et le numéro dans la colonne indique le décalage de cet octet. Le nom de la deuxième ligne de chaque chiffre correspond au nom d’une variable dans la déclaration. Les colonnes grisées indiquent le remplissage requis pour obtenir l’alignement spécifié.

#### <a name="example-1"></a>Exemple 1

```C
// Total size = 2 bytes, alignment = 2 bytes (word).

_declspec(align(2)) struct {
    short a;      // +0; size = 2 bytes
}
```

![Disposition de structure de l’exemple 1 de conversion AMD](../build/media/vcamd_conv_ex_1_block.png "AMD conversion exemple 1 structure de disposition")

#### <a name="example-2"></a>Exemple 2

```C
// Total size = 24 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) struct {
    int a;       // +0; size = 4 bytes
    double b;    // +8; size = 8 bytes
    short c;     // +16; size = 2 bytes
}
```

![Disposition de structure de l’exemple 2 de conversion AMD](../build/media/vcamd_conv_ex_2_block.png "disposition de structure de l’exemple 2 de conversion AMD")

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

![Disposition de structure de l’exemple 2 de conversion AMD](../build/media/vcamd_conv_ex_3_block.png "disposition de structure de l’exemple 2 de conversion AMD")

#### <a name="example-4"></a>Exemple 4

```C
// Total size = 8 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) union {
    char *p;      // +0; size = 8 bytes
    short s;      // +0; size = 2 bytes
    long l;       // +0; size = 4 bytes
}
```

![AMD conversion exemple 4 union layouit](../build/media/vcamd_conv_ex_4_block.png "layouit union des exemple 4 conversion AMD")

### <a name="bitfields"></a>Champs de bits

Champs de bits de structure sont limités à 64 bits et peut être de type signé int, unsigned int, int64 ou unsigned int64. Les champs de bits qui dépassent la limite de type ignorent les bits pour aligner le champ de bits de l’alignement de type suivant. Par exemple, les champs de bits entier ne peuvent pas dépasser une limite de 32 bits.

### <a name="conflicts-with-the-x86-compiler"></a>Est en conflit avec le x86 compilateur

Types de données qui sont supérieurs à 4 octets ne sont pas alignées automatiquement sur la pile lorsque vous utilisez le x86 compilateur de compiler une application. Étant donné que l’architecture pour le x86 compilateur est une pile alignée sur 4 octets, toute valeur supérieure à 4 octets, par exemple, un entier 64 bits, ne peut pas être alignée automatiquement à une adresse de 8 octets.

Utilisation des données non alignées a deux conséquences.

- Il peut prendre plus de temps à accéder à des emplacements non alignés que nécessaire pour accéder aux emplacements alignés.

- Emplacements non alignés ne peut pas être utilisés dans les opérations verrouillées.

Si vous avez besoin d’un alignement plus strict, utilisez `__declspec(align(N))` sur les déclarations de variable. Cela indique au compilateur d’aligner dynamiquement de la pile pour répondre à vos spécifications. Toutefois, ajuster de façon dynamique la pile au moment de l’exécution peut provoquer une exécution plus lente de votre application.

## <a name="register-usage"></a>Utilisation des registres

Le x64 architecture fournit pour 16 registres généraux (ci-après dénommés registres d’entiers) ainsi que 16 registres XMM/YMM inscrit disponibles pour une utilisation à virgule flottante. Les registres volatils sont des registres de travail censés être détruits après un appel. Les registres non volatils doivent conserver leurs valeurs tout au long d'un appel de fonction et être enregistrés par l'appelé s'il les utilise.

### <a name="register-volatility-and-preservation"></a>Inscrire la volatilité et préservation

Le tableau suivant explique comment chaque registre est utilisé dans les appels de fonction :

||||
|-|-|-|
|Registre|État|Utilisez|
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
|XMM0, YMM0|Volatil|Premier argument FP ; premier argument de type vectoriel quand `__vectorcall` est utilisé|
|XMM1, YMM1|Volatil|Deuxième argument FP ; deuxième argument de type vectoriel quand `__vectorcall` est utilisé|
|XMM2, YMM2|Volatil|Troisième argument FP ; troisième argument de type vectoriel quand `__vectorcall` est utilisé|
|XMM3, YMM3|Volatil|Quatrième argument FP ; quatrième argument de type vectoriel quand `__vectorcall` est utilisé|
|XMM4, YMM4|Volatil|Doit être conservé si nécessaire par l'appelant ; cinquième argument de type vectoriel quand `__vectorcall` est utilisé|
|XMM5, YMM5|Volatil|Doit être conservé si nécessaire par l'appelant ; sixième argument de type vectoriel quand `__vectorcall` est utilisé|
|XMM6:XMM15, YMM6:YMM15|Non volatil (XMM), volatil (moitié supérieure de YMM)|Doit être conservé par l’appelé. Les registres YMM doivent être conservés si nécessaire par l'appelant.|

Sur la sortie de la fonction et sur l’entrée de la fonction aux appels de la bibliothèque Runtime C et les appels de système de Windows, l’indicateur de direction de l’UC indicateurs register est censé être effacé.

## <a name="stack-usage"></a>Utilisation de la pile

Pour plus d’informations sur l’allocation de piles, alignement, les types de fonction et les frames de pile sur x64, consultez [x64 l’utilisation de la pile](stack-usage.md).

## <a name="prolog-and-epilog"></a>Prologue et épilogue

Chaque fonction qui alloue de l’espace de pile, appelle d’autres fonctions, enregistre les registres non volatils ou utilise la gestion des exceptions doit posséder un prologue dont les limites d’adresse sont décrites dans les données de déroulement associées à l’entrée de table de fonction correspondante et les épilogues à chaque sortie vers une fonction. Pour plus d’informations sur le prologue requis et le code d’épilogue sur x64, consultez [x64 prologue et épilogue](prolog-and-epilog.md).

## <a name="x64-exception-handling"></a>x64 la gestion des exceptions

Pour plus d’informations sur les conventions et les structures de données utilisées pour implémenter la gestion structurée des exceptions et le comportement sur le x64 des exceptions C++, consultez [x64 gestion des exceptions](exception-handling-x64.md).

## <a name="intrinsics-and-inline-assembly"></a>Assembly de fonctions intrinsèques et inline

Une des contraintes pour le x64 compilateur consiste à n’avoir aucune prise en charge d’assembleur inline. Cela signifie que les fonctions qui ne peuvent pas être écrits en C ou C++ doivent être écrites en tant que sous-routines ou fonctions intrinsèques prises en charge par le compilateur. Certaines fonctions sont sensibles aux performances et d’autres pas. Les fonctions sensibles aux performances doivent être implémentées comme fonctions intrinsèques.

Les fonctions intrinsèques prises en charge par le compilateur sont décrites dans [intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md).

## <a name="image-format"></a>Format d’image

Le x64 format d’image exécutable est PE32 +. Les images exécutables (DLL et exe) sont limitées à une taille maximale de 2 gigaoctets, afin de l’adressage relatif avec un déplacement 32 bits peut être utilisé pour traiter les données d’image statique. Ces données incluent la table des adresses d’importation, les constantes de chaîne, les données globales statiques et ainsi de suite.

## <a name="see-also"></a>Voir aussi

[Conventions d’appel](../cpp/calling-conventions.md)
