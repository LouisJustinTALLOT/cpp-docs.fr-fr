---
title: Convention d’appel x64
description: Détails de la Convention d’appel ABI x64 par défaut.
ms.date: 12/17/2018
ms.assetid: 41ca3554-b2e3-4868-9a84-f1b46e6e21d9
ms.openlocfilehash: 2cad00ac7f2cb5fe086fa262a0f512330997391f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856883"
---
# <a name="x64-calling-convention"></a>Convention d’appel x64

Cette section décrit les processus standard et les conventions qu’une fonction (l’appelant) utilise pour effectuer des appels dans une autre fonction (l’appelé) dans du code x64.

## <a name="calling-convention-defaults"></a>Valeurs par défaut de la Convention d’appel

L’interface binaire d’application x64 (ABI) utilise une convention d’appel rapide à quatre registres par défaut. L’espace est alloué sur la pile des appels en tant que magasin d’instantanés pour que les appelants enregistrent ces registres. Il existe une correspondance un-à-un stricte entre les arguments d’un appel de fonction et les registres utilisés pour ces arguments. Tout argument qui ne peut pas contenir plus de 8 octets, ou qui n’est pas 1, 2, 4 ou 8 octets, doit être passé par référence. Un argument unique n’est jamais réparti sur plusieurs registres. La pile de registres X87 est inutilisée et peut être utilisée par l’appelé, mais elle doit être considérée comme volatile entre les appels de fonction. Toutes les opérations à virgule flottante sont effectuées à l’aide des 16 registres XMM. Les arguments entiers sont passés dans les registres RCX, RDX, R8 et R9. Les arguments à virgule flottante sont passés dans XMM0L, XMM1L, XMM2L et XMM3L. les arguments de 16 octets sont passés par référence. Le passage de paramètres est décrit en détail dans [passage de paramètres](#parameter-passing). En plus de ces registres, RAX, R10, R11, XMM4 et XMM5 sont considérés comme volatiles. Tous les autres registres sont non volatils. L’utilisation des registres est documentée en détail dans la section utilisation des registres et registres enregistrés de [l'](../build/x64-software-conventions.md#register-usage) [appelant/appelé](#callercallee-saved-registers).

Pour les fonctions prototypées, tous les arguments sont convertis en types d’appel attendus avant de passer. L’appelant est chargé d’allouer de l’espace pour les paramètres à l’appelé, et doit toujours allouer suffisamment d’espace pour stocker quatre paramètres de Registre, même si l’appelé ne prend pas ce nombre de paramètres. Cette Convention simplifie la prise en charge des fonctions non prototypées du langage C et desC++ fonctions vararg c/functions. Pour les fonctions vararg ou non prototypées, toute valeur à virgule flottante doit être dupliquée dans le registre à usage général correspondant. Tous les paramètres au-delà des quatre premiers doivent être stockés sur la pile après le magasin d’instantanés avant l’appel. Les détails de la fonction vararg se trouvent dans [varargs](#varargs). Les informations sur les fonctions non prototypées sont détaillées dans les [fonctions non prototypées](#unprototyped-functions).

## <a name="alignment"></a>Alignment

La plupart des structures sont alignées sur leur alignement naturel. Les principales exceptions sont le pointeur de pile et `malloc` ou la mémoire `alloca`, qui sont alignées sur 16 octets afin d’aider les performances. L’alignement au-dessus de 16 octets doit être effectué manuellement, mais étant donné que 16 octets sont une taille d’alignement commune pour les opérations XMM, cette valeur doit fonctionner pour la plupart du code. Pour plus d’informations sur la disposition et l’alignement de la structure, consultez [types et stockage](../build/x64-software-conventions.md#types-and-storage). Pour plus d’informations sur la disposition de la pile, consultez Utilisation de la [pile x64](../build/stack-usage.md).

## <a name="unwindability"></a>La déroulabilité

Les fonctions feuilles sont des fonctions qui ne modifient pas les registres non volatiles. Une fonction non-feuille peut changer RSP non volatile, par exemple, en appelant une fonction ou en allouant un espace de pile supplémentaire pour les variables locales. Pour récupérer des registres non volatils lorsqu’une exception est gérée, les fonctions non-feuille doivent être annotées avec des données statiques qui décrivent comment dérouler correctement la fonction au niveau d’une instruction arbitraire. Ces données sont stockées sous la forme de *pData*, ou de données de procédure, qui, à leur tour, fait référence à *XData*, les données de gestion des exceptions. Le XData contient les informations de déroulement et peut pointer vers une fonction pData ou un gestionnaire d’exceptions supplémentaire. Les journaux et les épilogues sont très restreints afin qu’ils puissent être décrits correctement dans XData. Le pointeur de pile doit être aligné sur 16 octets dans toute région de code qui ne fait pas partie d’un épilogue ou d’un prologue, sauf dans les fonctions feuille. Les fonctions feuilles peuvent être déroulées simplement en simulant un retour, de sorte que pData et XData ne sont pas nécessaires. Pour plus d’informations sur la structure correcte des prologues de fonction et des épilogues, consultez [prologue et épilogue x64](../build/prolog-and-epilog.md). Pour plus d’informations sur la gestion des exceptions, ainsi que sur la gestion des exceptions et le déroulement des pData et XData, consultez [gestion des exceptions x64](../build/exception-handling-x64.md).

## <a name="parameter-passing"></a>Passage de paramètres

Les quatre premiers arguments entiers sont passés dans les registres. Les valeurs entières sont passées dans l’ordre de gauche à droite dans RCX, RDX, R8 et R9, respectivement. Les arguments cinq et supérieurs sont passés sur la pile. Tous les arguments sont justifiés à droite dans les registres. l’appelé peut donc ignorer les bits supérieurs du Registre et accéder uniquement à la partie du registre nécessaire.

Les arguments à virgule flottante et à double précision dans les quatre premiers paramètres sont passés dans XMM0-XMM3, en fonction de la position. Les registres d’entiers RCX, RDX, R8 et R9 qui seraient normalement utilisés pour ces positions sont ignorés, sauf dans le cas des arguments varargs. Pour plus d’informations, consultez [varargs](#varargs). De même, les registres XMM0-XMM3 sont ignorés lorsque l’argument correspondant est un type entier ou pointeur.

les types de [__m128](../cpp/m128.md) , les tableaux et les chaînes ne sont jamais passés par la valeur immédiate. Au lieu de cela, un pointeur est passé à la mémoire allouée par l’appelant. Les structs et les unions de taille 8, 16, 32 ou 64 bits, ainsi que les types de __m64, sont passés comme s’il s’agissait d’entiers de la même taille. Les structs ou les unions d’autres tailles sont passés comme pointeur vers la mémoire allouée par l’appelant. Pour ces types d’agrégats passés comme un pointeur, y compris \__m128, la mémoire temporaire allouée par l’appelant doit être alignée sur 16 octets.

Les fonctions intrinsèques qui n’allouent pas d’espace de pile et n’appellent pas d’autres fonctions, utilisent parfois d’autres registres volatiles pour passer des arguments Register supplémentaires. Cette optimisation est rendue possible par la liaison étroite entre le compilateur et l’implémentation de la fonction intrinsèque.

L’appelé est chargé de vider les paramètres de Registre dans leur espace d’ombre si nécessaire.

Le tableau suivant résume la façon dont les paramètres sont transmis :

|Type de paramètre|Réussite|
|--------------------|----------------|
|Virgule flottante|4 premiers paramètres-XMM0 à XMM3. D’autres ont réussi sur la pile.|
|Integer|4 premiers paramètres : RCX, RDX, R8, R9. D’autres ont réussi sur la pile.|
|Agrégats (8, 16, 32 ou 64 bits) et __m64|4 premiers paramètres : RCX, RDX, R8, R9. D’autres ont réussi sur la pile.|
|Agrégats (autres)|Par pointeur. 4 premiers paramètres passés comme pointeurs dans RCX, RDX, R8 et R9|
|__m128|Par pointeur. 4 premiers paramètres passés comme pointeurs dans RCX, RDX, R8 et R9|

### <a name="example-of-argument-passing-1---all-integers"></a>Exemple de passage d’argument 1-tous les entiers

```cpp
func1(int a, int b, int c, int d, int e);
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack
```

### <a name="example-of-argument-passing-2---all-floats"></a>Exemple de passage d’argument 2-tous les valeurs float

```cpp
func2(float a, double b, float c, double d, float e);
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack
```

### <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>Exemple d’argument passant 3-Mixed int et Floats

```cpp
func3(int a, double b, int c, float d);
// a in RCX, b in XMM1, c in R8, d in XMM3
```

### <a name="example-of-argument-passing-4--__m64-__m128-and-aggregates"></a>Exemple de passage d’argument 4-__m64, \__m128 et agrégats

```cpp
func4(__m64 a, _m128 b, struct c, float d);
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3
```

## <a name="varargs"></a>Varargs

Si les paramètres sont passés via les varargs (par exemple, les arguments de sélection), la Convention de passage de paramètre de Registre normale s’applique, y compris le débordement des cinquième et deuxième arguments de la pile. Il incombe à l’appelé de vider les arguments dont l’adresse est prise. Pour les valeurs à virgule flottante uniquement, le registre d’entiers et le registre à virgule flottante doivent contenir la valeur, au cas où l’appelé attende la valeur dans les registres d’entiers.

## <a name="unprototyped-functions"></a>Fonctions qui ne sont pas prototypées

Pour les fonctions qui ne sont pas entièrement prototypées, l’appelant passe des valeurs entières en tant qu’entiers et valeurs à virgule flottante en tant que double précision. Pour les valeurs à virgule flottante uniquement, le registre d’entiers et le registre à virgule flottante contiennent la valeur float au cas où l’appelé attende la valeur dans les registres d’entiers.

```cpp
func1();
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7
   func1(2, 1.0, 7);
}
```

## <a name="return-values"></a>Valeurs retournées

Une valeur de retour scalaire pouvant tenir dans 64 bits est retournée via RAX ; Cela comprend les types de __m64. Les types non scalaires, y compris les types float, double et Vector, comme [__m128](../cpp/m128.md), [__m128i](../cpp/m128i.md) [__m128d](../cpp/m128d.md) sont retournés dans XMM0. L'état des bits non utilisés dans la valeur retournée dans RAX ou XMM0 est non défini.

Les types définis par l'utilisateur peuvent être retournés par valeur depuis des fonctions globales et des fonctions de membres statiques. Pour retourner un type défini par l’utilisateur par valeur dans RAX, il doit avoir une longueur de 1, 2, 4, 8, 16, 32 ou 64 bits. Il ne doit pas non plus être un constructeur, un destructeur ou un opérateur d’assignation de copie défini par l’utilisateur ; aucune donnée membre non statique privée ou protégée ; aucun membre de données non statiques de type référence ; aucune classe de base ; aucune fonction virtuelle ; et aucun membre de données qui ne répond pas également à ces exigences. (Il s'agit essentiellement de la définition d'un type POD de C++ 03. Étant donné que la définition a changé dans la norme C++ 11, nous vous déconseillons d’utiliser `std::is_pod` pour ce test.) Dans le cas contraire, l’appelant assume la responsabilité d’allouer de la mémoire et de passer un pointeur pour la valeur de retour comme premier argument. Les arguments suivants sont décalés d’un argument vers la droite. Le même pointeur doit être retourné par l'appelé dans RAX.

Ces exemples montrent comment les paramètres et les valeurs de retour sont passés pour les fonctions avec les déclarations spécifiées :

### <a name="example-of-return-value-1---64-bit-result"></a>Exemple de valeur de retour 1-64 bits

```Output
__int64 func1(int a, float b, int c, int d, int e);
// Caller passes a in RCX, b in XMM1, c in R8, d in R9, e pushed on stack,
// callee returns __int64 result in RAX.
```

### <a name="example-of-return-value-2---128-bit-result"></a>Exemple de valeur de retour 2-128 bits

```Output
__m128 func2(float a, double b, int c, __m64 d);
// Caller passes a in XMM0, b in XMM1, c in R8, d in R9,
// callee returns __m128 result in XMM0.
```

### <a name="example-of-return-value-3---user-type-result-by-pointer"></a>Exemple de valeur de retour 3-type d’utilisateur résultat par pointeur

```Output
struct Struct1 {
   int j, k, l;    // Struct1 exceeds 64 bits.
};
Struct1 func3(int a, double b, int c, float d);
// Caller allocates memory for Struct1 returned and passes pointer in RCX,
// a in RDX, b in XMM2, c in R9, d pushed on the stack;
// callee returns pointer to Struct1 result in RAX.
```

### <a name="example-of-return-value-4---user-type-result-by-value"></a>Exemple de valeur de retour 4-résultat de type utilisateur par valeur

```Output
struct Struct2 {
   int j, k;    // Struct2 fits in 64 bits, and meets requirements for return by value.
};
Struct2 func4(int a, double b, int c, float d);
// Caller passes a in RCX, b in XMM1, c in R8, and d in XMM3;
// callee returns Struct2 result by value in RAX.
```

## <a name="callercallee-saved-registers"></a>Registres enregistrés de l’appelant/appelé

Les registres RAX, RCX, RDX, R8, R9, R10, R11, XMM0-5 et les parties supérieures des YMM0-15 et ZMM0-15 sont considérés comme volatiles et doivent être considérés comme étant détruits sur les appels de fonction (sauf en cas de sécurité Provable par analyse, par exemple l’optimisation de l’ensemble du programme). Sur AVX512VL, les registres ZMM, YMM et XMM 16-31 sont volatiles.

Les registres RBX, RBP, RDI, RSI, RSP, R12, R13, R14, R15 et XMM6-15 sont considérés comme non volatils et doivent être enregistrés et restaurés par une fonction qui les utilise.

## <a name="function-pointers"></a>Pointeurs fonction
 
Les pointeurs de fonction sont simplement des pointeurs vers l’étiquette de la fonction respective. Il n’existe aucune configuration de table des matières pour les pointeurs de fonction.

## <a name="floating-point-support-for-older-code"></a>Prise en charge de la virgule flottante pour le code plus ancien

Les registres de pile MMX et à virgule flottante (MM0-MM7/ST0-ST7) sont conservés entre les changements de contexte. Il n’existe aucune convention d’appel explicite pour ces registres. L’utilisation de ces registres est strictement interdite dans le code en mode noyau.

## <a name="fpcsr"></a>FpCsr

L’état du registre comprend également le mot de contrôle X87 FPU. La Convention d’appel impose à ce registre d’être non volatil.

L’inscription du mot de contrôle X87 FPU est définie sur les valeurs standard suivantes au début de l’exécution du programme :

| Inscrire\[bits] | Paramètre |
|-|-|
| FPCSR\[0:6] | L’exception masque tous les 1 (toutes les exceptions masquées) |
| FPCSR\[7] | Réservé-0 |
| FPCSR\[8:9] | Contrôle de précision-10 (précision double) |
| FPCSR\[10:11] | Contrôle d’arrondi-0 (arrondi au plus proche) |
| FPCSR\[12] | Contrôle infini-0 (non utilisé) |

Un appelé qui modifie l’un des champs dans FPCSR doit les restaurer avant de retourner à son appelant. En outre, un appelant qui a modifié l’un de ces champs doit les restaurer dans leurs valeurs standard avant d’appeler un appelé, sauf en cas d’accord, l’appelé attend les valeurs modifiées.

Il existe deux exceptions aux règles concernant la non-volatilité des indicateurs de contrôle :

1. Dans les fonctions où l’objectif documenté de la fonction donnée est de modifier les indicateurs FpCsr non volatils.

1. Lorsqu’il est prouvé que la violation de ces règles aboutit à un programme qui se comporte comme un programme dans lequel ces règles ne sont pas violées, par exemple, par le biais de l’analyse de l’ensemble du programme.

## <a name="mxcsr"></a>MxCsr

L’état du registre comprend également MxCsr. La Convention d’appel divise ce registre en une partie volatile et une partie non volatile. La partie volatile se compose des six indicateurs d’État, à MXCSR\[0:5], tandis que le reste du Registre, MXCSR\[6:15], est considéré comme non volatile.

La partie non volatile est définie sur les valeurs standard suivantes au début de l’exécution du programme :

| Inscrire\[bits] | Paramètre |
|-|-|
| MXCSR\[6] | Les dénormals sont des zéros-0 |
| MXCSR\[7:12] | L’exception masque tous les 1 (toutes les exceptions masquées) |
| MXCSR\[13:14] | Contrôle d’arrondi-0 (arrondi au plus proche) |
| MXCSR\[15] | Vidage sur zéro pour un dépassement de capacité négatif masqué-0 (désactivé) |

Un appelé qui modifie l’un des champs non volatils dans MXCSR doit les restaurer avant de retourner à son appelant. En outre, un appelant qui a modifié l’un de ces champs doit les restaurer dans leurs valeurs standard avant d’appeler un appelé, sauf en cas d’accord, l’appelé attend les valeurs modifiées.

Il existe deux exceptions aux règles concernant la non-volatilité des indicateurs de contrôle :

- Dans les fonctions où l’objectif documenté de la fonction donnée est de modifier les indicateurs MxCsr non volatils.

- Lorsqu’il est prouvé que la violation de ces règles aboutit à un programme qui se comporte comme un programme dans lequel ces règles ne sont pas violées, par exemple, par le biais de l’analyse de l’ensemble du programme.

Aucune hypothèse ne peut être faite sur l’état de la partie volatile de MXCSR à travers une limite de fonction, sauf si elle est spécifiquement décrite dans la documentation d’une fonction.

## <a name="setjmplongjmp"></a>setjmp/longjmp

Quand vous incluez setjmpex. h ou setjmp. h, tous les appels à [setjmp](../c-runtime-library/reference/setjmp.md) ou [longjmp](../c-runtime-library/reference/longjmp.md) entraînent un déroulement qui appelle des destructeurs et des appels de `__finally`.  Cela diffère de x86, où l’inclusion de setjmp. h génère des clauses de `__finally` et des destructeurs qui ne sont pas appelés.

Un appel à `setjmp` conserve le pointeur de pile actuel, les registres non volatiles et les registres MxCsr.  Les appels à `longjmp` revenir au site d’appel de `setjmp` le plus récent et rétablit le pointeur de pile, les registres non volatiles et les registres MxCsr à l’état préservé par l’appel de `setjmp` le plus récent.

## <a name="see-also"></a>Voir aussi

[Conventions des logiciels x64](../build/x64-software-conventions.md)
