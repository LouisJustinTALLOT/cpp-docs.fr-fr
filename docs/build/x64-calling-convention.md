---
title: Convention d’appel x64
description: Détails de la convention d’appel par défaut x64 ABI.
ms.date: 12/17/2018
ms.assetid: 41ca3554-b2e3-4868-9a84-f1b46e6e21d9
ms.openlocfilehash: 2cad00ac7f2cb5fe086fa262a0f512330997391f
ms.sourcegitcommit: 0e3da5cea44437c132b5c2ea522bd229ea000a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67861166"
---
# <a name="x64-calling-convention"></a>Convention d’appel x64

Cette section décrit les processus standards et les conventions utilisées par une fonction (l’appelant) pour effectuer des appels dans une autre fonction (l’appelé) dans x64 code.

## <a name="calling-convention-defaults"></a>Appel des valeurs par défaut de la convention

Le x64 Interface binaire d’Application (ABI) utilise une Registre de quatre fast-convention d’appel par valeur par défaut. Espace est alloué sur la pile des appels pour appelés enregistrer ces registres stocker les clichés instantanés. Il existe une correspondance unique stricte entre les arguments pour un appel de fonction et les registres utilisés pour ces arguments. Tout argument qui ne tient pas dans 8 octets, ou n’est pas 1, 2, 4 ou 8 octets, doit être passé par référence. Un seul argument n’est jamais réparti sur plusieurs registres. Pile de registres le x87 n’est pas utilisé et peuvent être utilisés par l’appelé, mais doit être considérée comme volatile entre les appels de fonction. Virgule flottante toutes les opérations sont effectuées à l’aide de la 16 registres XMM s’inscrit. Arguments entiers sont passés dans les registres RCX, RDX, R8 et R9. Arguments sont passés dans XMM0L, XMM1L, XMM2L et XMM3L de virgule flottante. arguments de 16 octets sont passés par référence. Passage de paramètres est décrit en détail dans [passage de paramètres](#parameter-passing). Outre ces registres, RAX, R10, R11, XMM4 et XMM5 sont considérés comme volatile. Tous les autres registres sont non volatiles. L’utilisation des registres est présentée en détail dans [inscrire Usage](../build/x64-software-conventions.md#register-usage) et [appelant/appelé enregistré inscrit](#callercallee-saved-registers).

Pour les fonctions prototypées, tous les arguments sont convertis aux types appelés attendus avant d’être transféré. L’appelant est responsable de l’allocation d’espace pour les paramètres à l’appelé et doit toujours allouer suffisamment d’espace pour stocker les quatre paramètres de Registre, même si l’appelé ne prend pas autant de paramètres. Cette convention simplifie la prise en charge pour les fonctions non prototypées en langage C et les fonctions vararg C/C++. Pour les fonctions vararg ou non prototypées, virgule flottante valeurs doit être dupliqué dans le Registre à usage général correspondant. Tous les paramètres au-delà des quatre premiers doivent être stockés sur la pile une fois que l’ombre stocker avant l’appel. Vous trouverez les détails de la fonction vararg dans [Varargs](#varargs). Informations sur les fonctions non prototypées sont détaillées dans [fonctions non prototypées](#unprototyped-functions).

## <a name="alignment"></a>Alignement

La plupart des structures sont alignées sur leur alignement naturel. Les principales exceptions sont le pointeur de pile et `malloc` ou `alloca` mémoire, ce qui est aligné sur 16 octets pour de meilleures performances. Alignement supérieur à 16 octets doit être effectué manuellement, mais puisque 16 octets est une taille d’alignement courantes pour les opérations XMM, cette valeur doit fonctionner pour la plupart du code. Pour plus d’informations sur la disposition de la structure et l’alignement, consultez [Types et stockage](../build/x64-software-conventions.md#types-and-storage). Pour plus d’informations sur la disposition de pile, consultez [x64 l’utilisation de la pile](../build/stack-usage.md).

## <a name="unwindability"></a>Capacité de déroulement

Fonctions de feuille sont des fonctions qui ne changent pas les registres non volatils. Une fonction non terminaux peut changer RSP non volatile, par exemple, en appelant une fonction ou de l’allocation d’espace de pile supplémentaires pour les variables locales. Pour récupérer les registres non volatils lorsqu’une exception est gérée, les fonctions non feuille doivent être annotées avec des données statiques qui décrit comment dérouler correctement la fonction à une instruction arbitraire. Ces données sont stockées en tant que *pdata*, ou les données de procédure, qui à son tour fait référence à *xdata*, les données de gestion des exceptions. Le xdata contient les informations de déroulement et peut pointer vers pdata supplémentaire ou une fonction de gestionnaire d’exception. Les prologues et épilogues sont très restreinte afin qu’ils peuvent être décrits correctement dans xdata. Le pointeur de pile doit être aligné sur n’importe quelle région de code qui ne fait pas partie d’un épilogue ou d’un prologue, sauf dans les fonctions de feuille de 16 octets. Fonctions de feuille peuvent être vidées simplement en simulant un retour, pdata et xdata sont donc pas nécessaires. Pour plus d’informations sur la structure appropriée des prologues de fonction et épilogues, consultez [x64 prologue et épilogue](../build/prolog-and-epilog.md). Pour plus d’informations sur la gestion des exceptions et la gestion des exceptions et déroulement de pdata et xdata, consultez [x64 gestion des exceptions](../build/exception-handling-x64.md).

## <a name="parameter-passing"></a>Passage de paramètres

Les quatre premiers arguments entiers sont passés dans les registres. Valeurs entières sont passées dans l’ordre de gauche à droite dans RCX, RDX, R8 et R9, respectivement. Arguments cinq ou supérieur sont passés sur la pile. Tous les arguments sont alignés à droite dans les registres, donc l’appelé peut ignorer les bits supérieurs du Registre et accéder uniquement la partie du Registre nécessaires.

Tous les arguments à virgule flottante et double précision dans les quatre premiers paramètres sont passés dans XMM0 - XMM3, en fonction de la position. Les registres d’entiers RCX, RDX, R8 et R9 doit normalement être utilisé pour les postes sont ignorés, sauf dans le cas des arguments de varargs. Pour plus d’informations, consultez [Varargs](#varargs). De même, le XMM0 - XMM3 registres sont ignorés lorsque l’argument correspondant est un type entier ou pointeur.

[__m128](../cpp/m128.md) types, les tableaux et les chaînes ne sont jamais passés par valeur immédiate. Au lieu de cela, un pointeur est passé à la mémoire allouée par l’appelant. Structs et unions de taille 8, 16, 32 ou 64 bits et les types __m64, sont transmies comme s’il s’agissait d’entiers de la même taille. Les structures ou unions d’autres tailles sont passées en tant que pointeur vers la mémoire allouée par l’appelant. Pour ces types d’agrégats passés en tant que pointeur, y compris \__m128, la mémoire temporaire allouée par l’appelant doit être alignée sur 16 octets.

Les fonctions intrinsèques qui ne pas allouer de l’espace de pile et n’appellent d’autres fonctions utilisent parfois des autres registres volatils pour passer des arguments de Registre supplémentaires. Cette optimisation est rendue possible par la liaison étroite entre le compilateur et l’implémentation de la fonction intrinsèque.

L’appelant est responsable pour vider les paramètres de Registre dans leur espace de clichés instantanés, si nécessaire.

Le tableau suivant résume la façon dont les paramètres sont passés :

|Type de paramètre|Mode de passage|
|--------------------|----------------|
|Virgule flottante|Tout d’abord 4 paramètres - XMM0 à XMM3. Autres sont passés sur la pile.|
|Entier|Tout d’abord 4 paramètres - RCX, RDX, R8, R9. Autres sont passés sur la pile.|
|Agrégats (8, 16, 32 ou 64 bits) et __m64|Tout d’abord 4 paramètres - RCX, RDX, R8, R9. Autres sont passés sur la pile.|
|Agrégats (autre)|Par pointeur. 4 premiers paramètres passés comme pointeurs dans RCX, RDX, R8 et R9.|
|__m128|Par pointeur. 4 premiers paramètres passés comme pointeurs dans RCX, RDX, R8 et R9.|

### <a name="example-of-argument-passing-1---all-integers"></a>Exemple de 1 - tous les entiers de passage d’arguments

```cpp
func1(int a, int b, int c, int d, int e);
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack
```

### <a name="example-of-argument-passing-2---all-floats"></a>Exemple d’argument qui passe 2 - toutes les valeurs en virgule flottante

```cpp
func2(float a, double b, float c, double d, float e);
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack
```

### <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>Exemple d’argument qui passe 3 - ints mixte et à virgule flottante

```cpp
func3(int a, double b, int c, float d);
// a in RCX, b in XMM1, c in R8, d in XMM3
```

### <a name="example-of-argument-passing-4--m64-m128-and-aggregates"></a>Exemple d’argument qui passe 4-__m64, \__m128 et des agrégats

```cpp
func4(__m64 a, _m128 b, struct c, float d);
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3
```

## <a name="varargs"></a>Varargs

Si des paramètres sont passés par le biais de varargs (par exemple, les arguments de points de suspension), puis la convention de passage de paramètres de Registre normale s’applique, y compris le dépassement des arguments cinquième et ultérieures à la pile. Il incombe l’appelé aux arguments de vidage qui ont leur adresse est acceptée. Pour les valeurs à virgule flottante, le Registre entier et le Registre à virgule flottante doivent contenir la valeur, si l’appelé attend la valeur dans les registres d’entiers.

## <a name="unprototyped-functions"></a>Fonctions non prototypées

Pour les fonctions pas entièrement prototypées, l’appelant transmet les valeurs entières en tant que nombres entiers et des valeurs à virgule flottante en tant que double précision. Pour les valeurs à virgule flottante, le Registre entier et le Registre à virgule flottante contiennent la valeur float si l’appelé attend la valeur dans les registres d’entiers.

```cpp
func1();
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7
   func1(2, 1.0, 7);
}
```

## <a name="return-values"></a>Valeurs de retour

Valeur de retour scalaire qui s’adapte à 64 bits est retournée via RAX ; Cela inclut les types __m64. Les types non scalaires, y compris les valeurs float, double et types de vecteur, tels que [__m128](../cpp/m128.md), [__m128i](../cpp/m128i.md), [__m128d](../cpp/m128d.md) sont retournées dans XMM0. L'état des bits non utilisés dans la valeur retournée dans RAX ou XMM0 est non défini.

Les types définis par l'utilisateur peuvent être retournés par valeur depuis des fonctions globales et des fonctions de membres statiques. Pour retourner un type défini par l’utilisateur par valeur dans RAX, il doit avoir une longueur de 1, 2, 4, 8, 16, 32 ou 64 bits. Il ne doit également avoir aucun constructeur défini par l’utilisateur, un destructeur ou un opérateur d’assignation de copie ; Aucun membre des données non statiques privé ou protégé ; Aucun membre de données non statiques de type référence ; aucune classe de base ; aucune fonction virtuelle ; et aucun membre de données qui ne répondent pas également à ces exigences. (Il s'agit essentiellement de la définition d'un type POD de C++ 03. Étant donné que la définition a changé dans la norme C ++ 11, nous déconseillons l’utilisation `std::is_pod` pour ce test.) Sinon, l’appelant prend la responsabilité d’allouer de la mémoire et de passer un pointeur pour la valeur de retour comme premier argument. Les arguments suivants sont décalés d’un argument vers la droite. Le même pointeur doit être retourné par l'appelé dans RAX.

Ces exemples montrent comment les paramètres et les valeurs de retour sont passés pour les fonctions avec les déclarations spécifiées :

### <a name="example-of-return-value-1---64-bit-result"></a>Exemple de valeur de retour 1 : résultat sur 64 bits

```Output
__int64 func1(int a, float b, int c, int d, int e);
// Caller passes a in RCX, b in XMM1, c in R8, d in R9, e pushed on stack,
// callee returns __int64 result in RAX.
```

### <a name="example-of-return-value-2---128-bit-result"></a>Exemple de valeur de retour 2 : résultat sur 128 bits

```Output
__m128 func2(float a, double b, int c, __m64 d);
// Caller passes a in XMM0, b in XMM1, c in R8, d in R9,
// callee returns __m128 result in XMM0.
```

### <a name="example-of-return-value-3---user-type-result-by-pointer"></a>Exemple de valeur de retour 3 : résultat de type utilisateur par pointeur

```Output
struct Struct1 {
   int j, k, l;    // Struct1 exceeds 64 bits.
};
Struct1 func3(int a, double b, int c, float d);
// Caller allocates memory for Struct1 returned and passes pointer in RCX,
// a in RDX, b in XMM2, c in R9, d pushed on the stack;
// callee returns pointer to Struct1 result in RAX.
```

### <a name="example-of-return-value-4---user-type-result-by-value"></a>Exemple de valeur de retour 4 : résultat de type utilisateur par valeur

```Output
struct Struct2 {
   int j, k;    // Struct2 fits in 64 bits, and meets requirements for return by value.
};
Struct2 func4(int a, double b, int c, float d);
// Caller passes a in RCX, b in XMM1, c in R8, and d in XMM3;
// callee returns Struct2 result by value in RAX.
```

## <a name="callercallee-saved-registers"></a>Registres enregistrés des appelants/appelés

Les registres RAX, RCX, RDX, R8, R9, R10, R11, XMM0-5 et les parties supérieures de YMM0-15 et ZMM0-15 sont considérés comme volatile et doivent être considéré comme détruit lors des appels de fonction (sauf si sinon sécurité-démontrables par analyse telles que de l’optimisation de l’ensemble du programme). Sur AVX512VL, les registres XMM ZMM et YMM 16-31 sont volatiles.

Les registres RBX, RBP, RDI, RSI, RSP, R12, R13, R14, R15 et XMM6-15 sont considérés comme non volatile et doivent être enregistrés et restauré par une fonction qui les utilise.

## <a name="function-pointers"></a>Pointeurs fonction
 
Les pointeurs fonction sont simplement des pointeurs vers l’étiquette de la fonction correspondante. Il n’y a aucune table des exigences de contenu (table des matières) pour les pointeurs de fonction.

## <a name="floating-point-support-for-older-code"></a>Prise en charge à virgule flottante pour le code plus ancien

Les registres MMX et pile à virgule flottante (MM0-MM7/ST0-ST7) sont conservés entre les commutateurs de contexte. Il n’existe aucune convention d’appel explicite pour ces registres. L’utilisation de ces registres est strictement interdite dans le code en mode noyau.

## <a name="fpcsr"></a>FpCsr

L’état du Registre inclut également le x87 mot de contrôle FPU. La convention d’appel définit ce Registre comme non volatil.

Le x87 Registre du mot de contrôle FPU est défini sur les valeurs standards suivantes au début de l’exécution du programme :

| Inscrire\[bits] | Paramètre |
|-|-|
| FPCSR\[0:6] | Exception masque tous les 1 (toutes les exceptions sont masquées) |
| FPCSR\[7] | Réservé - 0 |
| FPCSR\[8:9] | Contrôle de précision - 10 b (double précision) |
| FPCSR\[10:11] | Contrôle arrondi - 0 (arrondi à la plus proche) |
| FPCSR\[12] | Contrôle de l’infini - 0 (non utilisé) |

Un appelant qui modifie l’un des champs dans FPCSR doit restaurer avant de retourner à son appelant. En outre, un appelant qui a modifié l’un de ces champs doit les restaurer à leurs valeurs standards avant d’appeler un appelant, sauf si le contrat de l’appelé attend les valeurs modifiées.

Il existe deux exceptions aux règles sur la rémanence des indicateurs de contrôle :

1. Dans les fonctions dont l’objectif de la fonction donnée documenté consiste à modifier le MxFpCsrCsr non volatile indicateurs.

1. Lorsqu’il est prouvé corriger que les résultats de la violation de ces règles dans un programme qui se comporte comme un programme où ces règles ne sont pas violées, par exemple, via l’analyse de la totalité du programme.

## <a name="mxcsr"></a>MxCsr

L’état du Registre inclut également MxCsr. La convention d’appel divise ce Registre en une partie volatile et une partie non volatile. La partie volatile se compose des indicateurs de six état, dans le Registre MXCSR\[0:5], tandis que le reste du Registre, MXCSR\[6:15], est considéré comme non volatile.

La partie non volatile est définie sur les valeurs standards suivantes au début de l’exécution du programme :

| Inscrire\[bits] | Paramètre |
|-|-|
| MXCSR\[6] | Anomalies sont des zéros non significatifs - 0 |
| MXCSR\[7:12] | Exception masque tous les 1 (toutes les exceptions sont masquées) |
| MXCSR\[13:14] | Contrôle arrondi - 0 (arrondi à la plus proche) |
| MXCSR\[15] | Vider sur zéro pour le dépassement de capacité négatif masqué - 0 (désactivée) |

Un appelant qui modifie l’un des champs non volatiles dans MXCSR doit restaurer avant de retourner à son appelant. En outre, un appelant qui a modifié l’un de ces champs doit les restaurer à leurs valeurs standards avant d’appeler un appelant, sauf si le contrat de l’appelé attend les valeurs modifiées.

Il existe deux exceptions aux règles sur la rémanence des indicateurs de contrôle :

- Dans les fonctions dont l’objectif de la fonction donnée documenté consiste à modifier le Registre MxCsr non volatil indicateurs.

- Lorsqu’il est prouvé corriger que les résultats de la violation de ces règles dans un programme qui se comporte comme un programme où ces règles ne sont pas violées, par exemple, via l’analyse de la totalité du programme.

Aucune hypothèse ne peut être effectuée concernant l’état de la partie volatile de MXCSR au-delà d’une limite de fonction, sauf spécification contraire dans la documentation d’une fonction.

## <a name="setjmplongjmp"></a>setjmp/longjmp

Lorsque vous incluez setjmpex.h ou setjmp.h, tous les appels à [setjmp](../c-runtime-library/reference/setjmp.md) ou [longjmp](../c-runtime-library/reference/longjmp.md) entraînent un déroulement qui appelle des destructeurs et `__finally` appels.  Cela diffère de x86, où setjmp.h notamment entraîne `__finally` clauses et les destructeurs ne pas invoquées.

Un appel à `setjmp` conserve le pointeur de pile actuel, les registres non volatils et les registres MxCsr.  Les appels à `longjmp` retour à la plus récente `setjmp` appeler le site et réinitialise le pointeur de pile, les registres non volatils et les MxCsr inscrit, à l’état préservé par la plus récente `setjmp` appeler.

## <a name="see-also"></a>Voir aussi

[Conventions des logiciels x64](../build/x64-software-conventions.md)
