---
title: Convention d’appel x64
description: Détails de la convention d’appel par défaut x64 ABI.
ms.date: 12/17/2018
ms.assetid: 41ca3554-b2e3-4868-9a84-f1b46e6e21d9
ms.openlocfilehash: caf22172ea5e9c20280bce8e508d72fd30c00c5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335127"
---
# <a name="x64-calling-convention"></a>Convention d’appel x64

Cette section décrit les processus et conventions standard qu’une fonction (l’appelant) utilise pour faire des appels dans une autre fonction (la callee) dans le code x64.

## <a name="calling-convention-defaults"></a>Appel par défaut de convention

L’interface binaire d’application x64 (ABI) utilise par défaut une convention d’appel rapide à quatre registres. L’espace est alloué sur la pile d’appels comme un magasin d’ombre pour les appelants pour enregistrer ces registres. Il y a une correspondance individuelle stricte entre les arguments à un appel de fonction et les registres utilisés pour ces arguments. Tout argument qui ne rentre pas dans 8 octets, ou n’est pas 1, 2, 4, ou 8 octets, doit être adopté par référence. Un seul argument n’est jamais réparti entre plusieurs registres. La pile de registre x87 n’est pas utilisée et peut être utilisée par le callee, mais doit être considérée comme volatile entre les appels de fonction. Toutes les opérations de point flottant sont effectuées à l’aide des 16 registres XMM. Les arguments d’Integer sont passés dans les registres RCX, RDX, R8 et R9. Les arguments de points flottants sont passés dans XMM0L, XMM1L, XMM2L, et XMM3L. Les arguments 16-byte sont adoptés par référence. Le passage de paramètres est décrit en détail dans [Le passage de paramètres](#parameter-passing). En plus de ces registres, RAX, R10, R11, XMM4 et XMM5 sont considérés comme volatils. Tous les autres registres ne sont pas volatils. L’utilisation du registre est documentée en détail dans les registres [d’utilisation](../build/x64-software-conventions.md#register-usage) du registre et [d’enregistrement enregistré par l’appelant/appelant.](#callercallee-saved-registers)

Pour les fonctions prototypes, tous les arguments sont convertis aux types de callee attendus avant de passer. L’appelant est responsable de l’attribution de l’espace pour les paramètres au callee, et doit toujours allouer suffisamment d’espace pour stocker quatre paramètres d’enregistrement, même si le callee ne prend pas autant de paramètres. Cette convention simplifie le soutien aux fonctions non prototyped en C et aux fonctions vararg C/CMD. Pour les fonctions vararg ou non stéréotypées, toute valeur de point flottant doit être reproduite dans le registre général correspondant. Tous les paramètres au-delà des quatre premiers doivent être stockés sur la pile après le magasin d’ombre avant l’appel. Les détails de la fonction Vararg peuvent être trouvés dans [Varargs](#varargs). Les informations sur les fonctions non prorétotypes sont détaillées dans [les fonctions non prototypes](#unprototyped-functions).

## <a name="alignment"></a>Alignment

La plupart des structures sont alignées à leur alignement naturel. Les principales exceptions sont `malloc` le `alloca` pointeur de pile et ou la mémoire, qui sont alignés à 16 octets afin d’aider à la performance. L’alignement au-dessus de 16 octets doit être fait manuellement, mais puisque 16 octets est une taille d’alignement commune pour les opérations XMM, cette valeur devrait fonctionner pour la plupart du code. Pour plus d’informations sur la disposition de la structure et l’alignement, voir [Types et Stockage](../build/x64-software-conventions.md#types-and-storage). Pour plus d’informations sur la disposition de la pile, voir [l’utilisation de la pile x64](../build/stack-usage.md).

## <a name="unwindability"></a>Insevisibilité

Les fonctions de feuilles sont des fonctions qui ne modifient aucun registre non volatil. Une fonction non feuille peut modifier le RER non volatil, par exemple en appelant une fonction ou en allouant de l’espace supplémentaire pour les variables locales. Afin de récupérer les registres non volatils lorsqu’une exception est traitée, les fonctions non feuille doivent être annotées avec des données statiques qui décrivent comment bien dénouer la fonction à une instruction arbitraire. Ces données sont stockées sous *forme de pdata*, ou de données de procédure, qui se réfèrent à *xdata*, les données de traitement d’exception. La xdata contient les informations de dénouement, et peut indiquer une pdata supplémentaire ou une fonction de gestionnaire d’exception. Les prologes et les épilogues sont très restreints afin qu’ils puissent être correctement décrits dans xdata. Le pointeur de pile doit être aligné à 16 octets dans n’importe quelle région de code qui ne fait pas partie d’un épilog ou d’un prolog, sauf dans les fonctions de feuille. Les fonctions de feuille peuvent être dénouées simplement en simulant un retour, de sorte que pdata et xdata ne sont pas nécessaires. Pour plus de détails sur la structure appropriée des prologs de fonction et des épilogues, voir [x64 prolog et épilog](../build/prolog-and-epilog.md). Pour plus d’informations sur le traitement des exceptions, et la manipulation et le dénouement des pdata et xdata, voir [x64 traitement d’exception](../build/exception-handling-x64.md).

## <a name="parameter-passing"></a>Passage de paramètres

Les quatre premiers arguments sont adoptés dans les registres. Les valeurs integer sont passées dans l’ordre gauche-à-droite dans RCX, RDX, R8, et R9, respectivement. Les arguments cinq et plus sont passés sur la pile. Tous les arguments sont justifiés dans les registres, de sorte que le appelant peut ignorer les parties supérieures du registre et accéder uniquement à la partie du registre nécessaire.

Tous les arguments de point flottant et de double précision dans les quatre premiers paramètres sont passés en XMM0 - XMM3, selon la position. Les registres d’integer RCX, RDX, R8 et R9 qui seraient normalement utilisés pour ces positions sont ignorés, sauf dans le cas des arguments de varargs. Pour plus de détails, voir [Varargs](#varargs). De même, les registres XMM0 - XMM3 sont ignorés lorsque l’argument correspondant est un type d’integer ou de pointeur.

[__m128](../cpp/m128.md) types, tableaux et cordes ne sont jamais passés par valeur immédiate. Au lieu de cela, un pointeur est passé à la mémoire allouée par l’appelant. Les structs et les syndicats de taille 8, 16, 32 ou 64 bits, et __m64 types, sont adoptés comme s’ils étaient desintégriers de la même taille. Les structs ou les syndicats d’autres tailles sont adoptés comme pointeur de mémoire attribué par l’appelant. Pour ces types agrégés passés \_comme pointeur, y compris _m128, la mémoire temporaire allouée par l’appelant doit être alignée à 16 ans.

Fonctions intrinsèques qui n’allouent pas d’espace de pile, et n’appellent pas d’autres fonctions, parfois utiliser d’autres registres volatils pour passer des arguments de registre supplémentaires. Cette optimisation est rendue possible par la liaison serrée entre le compilateur et la mise en œuvre intrinsèque de la fonction.

Le callee est responsable du dumping des paramètres du registre dans son espace d’ombre si nécessaire.

Le tableau suivant résume la façon dont les paramètres sont adoptés :

|Type de paramètre|Comment passé|
|--------------------|----------------|
|Virgule flottante|Premiers 4 paramètres - XMM0 à XMM3. D’autres passèrent sur la pile.|
|Integer|Premiers 4 paramètres - RCX, RDX, R8, R9. D’autres passèrent sur la pile.|
|Agrégats (8, 16, 32 ou 64 bits) et __m64|Premiers 4 paramètres - RCX, RDX, R8, R9. D’autres passèrent sur la pile.|
|Agrégats (autres)|Par pointeur. Les 4 premiers paramètres sont passés comme pointeurs dans RCX, RDX, R8 et R9|
|__m128|Par pointeur. Les 4 premiers paramètres sont passés comme pointeurs dans RCX, RDX, R8 et R9|

### <a name="example-of-argument-passing-1---all-integers"></a>Exemple d’argument passant 1 - tous les entiers

```cpp
func1(int a, int b, int c, int d, int e);
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack
```

### <a name="example-of-argument-passing-2---all-floats"></a>Exemple d’argument passant 2 - tous les flotteurs

```cpp
func2(float a, double b, float c, double d, float e);
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack
```

### <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>Exemple d’argument passant 3 - ints mélangés et flotteurs

```cpp
func3(int a, double b, int c, float d);
// a in RCX, b in XMM1, c in R8, d in XMM3
```

### <a name="example-of-argument-passing-4--__m64-__m128-and-aggregates"></a>Exemple d’argumentation passant 4 \_-__m64, _m128 et agrégats

```cpp
func4(__m64 a, _m128 b, struct c, float d);
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3
```

## <a name="varargs"></a>Varargs

Si les paramètres sont adoptés par l’intermédiaire de varargs (par exemple, les arguments d’élipsis), alors le paramètre normal de passage de convention s’applique, y compris le déversement des arguments cinquième et suivant à la pile. C’est la responsabilité de l’appelant de jeter des arguments qui ont leur adresse prise. Pour les valeurs à points flottants seulement, le registre des integers et le registre des points flottants doivent contenir la valeur, au cas où le callee s’attend à la valeur dans les registres de l’intégrant.

## <a name="unprototyped-functions"></a>Fonctions non proméotypes

Pour les fonctions non entièrement prototypes, l’appelant passe des valeurs integer comme des intégrants et des valeurs de point flottant comme double précision. Pour les valeurs à points flottants seulement, le registre des integers et le registre des points flottants contiennent la valeur flottante au cas où le callee s’attend à la valeur dans les registres de l’intégrant.

```cpp
func1();
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7
   func1(2, 1.0, 7);
}
```

## <a name="return-values"></a>Valeurs retournées

Une valeur de retour scalaire qui peut s’adapter à 64 bits est retournée par RAX; cela comprend les types de __m64. Les types non-scalaires, y compris les flotteurs, les doubles et les vecteurs tels que [les __m128,](../cpp/m128.md) [__m128i,](../cpp/m128i.md) [__m128d](../cpp/m128d.md) sont retournés dans XMM0. L'état des bits non utilisés dans la valeur retournée dans RAX ou XMM0 est non défini.

Les types définis par l'utilisateur peuvent être retournés par valeur depuis des fonctions globales et des fonctions de membres statiques. Pour retourner un type défini par l’utilisateur par valeur dans RAX, il doit avoir une longueur de 1, 2, 4, 8, 16, 32, ou 64 bits. Il ne doit pas non plus avoir de constructeur, de destructeur ou d’opérateur d’affectation de copie défini par l’utilisateur; pas de membres privés ou protégés de données non statiques; pas de données non statiques membres de type de référence; pas de classes de base; pas de fonctions virtuelles; et aucun membre de données qui ne satisfont pas à ces exigences. (Il s'agit essentiellement de la définition d'un type POD de C++ 03. Étant donné que la définition a changé dans la norme C `std::is_pod` 11, nous ne recommandons pas d’utiliser pour ce test.) Dans le cas contraire, l’appelant assume la responsabilité d’attribuer la mémoire et de passer un pointeur pour la valeur de retour comme premier argument. Les arguments suivants sont décalés d’un argument vers la droite. Le même pointeur doit être retourné par l'appelé dans RAX.

Ces exemples montrent comment les paramètres et les valeurs de retour sont passés pour les fonctions avec les déclarations spécifiées :

### <a name="example-of-return-value-1---64-bit-result"></a>Exemple de valeur de rendement 1 - 64 bits

```Output
__int64 func1(int a, float b, int c, int d, int e);
// Caller passes a in RCX, b in XMM1, c in R8, d in R9, e pushed on stack,
// callee returns __int64 result in RAX.
```

### <a name="example-of-return-value-2---128-bit-result"></a>Exemple de valeur de rendement 2 - 128 bits

```Output
__m128 func2(float a, double b, int c, __m64 d);
// Caller passes a in XMM0, b in XMM1, c in R8, d in R9,
// callee returns __m128 result in XMM0.
```

### <a name="example-of-return-value-3---user-type-result-by-pointer"></a>Exemple de valeur de retour 3 - résultat de type utilisateur par pointeur

```Output
struct Struct1 {
   int j, k, l;    // Struct1 exceeds 64 bits.
};
Struct1 func3(int a, double b, int c, float d);
// Caller allocates memory for Struct1 returned and passes pointer in RCX,
// a in RDX, b in XMM2, c in R9, d pushed on the stack;
// callee returns pointer to Struct1 result in RAX.
```

### <a name="example-of-return-value-4---user-type-result-by-value"></a>Exemple de valeur de rendement 4 - résultat de type utilisateur par valeur

```Output
struct Struct2 {
   int j, k;    // Struct2 fits in 64 bits, and meets requirements for return by value.
};
Struct2 func4(int a, double b, int c, float d);
// Caller passes a in RCX, b in XMM1, c in R8, and d in XMM3;
// callee returns Struct2 result by value in RAX.
```

## <a name="callercallee-saved-registers"></a>Registres enregistrés de l’appelant/Callee

Les registres RAX, RCX, RDX, R8, R9, R10, R11, XMM0-5 et les parties supérieures de YMM0-15 et ZMM0-15 sont considérées comme volatiles et doivent être considérées comme détruites sur les appels de fonction (à moins que la sécurité autrement prouvable par des analyses telles que l’optimisation complète des programmes). Sur AVX512VL, les registres ZMM, YMM et XMM 16-31 sont volatils.

Les registres RBX, RBP, RDI, RSI, RSP, R12, R13, R14, R15 et XMM6-15 sont considérés comme nonvolatiles et doivent être sauvés et restaurés par une fonction qui les utilise.

## <a name="function-pointers"></a>Pointeurs fonction

Les pointeurs de fonction sont simplement des pointeurs à l’étiquette de la fonction respective. Il n’y a pas de tableau des exigences de contenu (TOC) pour les pointeurs de fonction.

## <a name="floating-point-support-for-older-code"></a>Soutien à point flottant pour un code plus ancien

Les registres MMX et pile à points flottants (MM0-MM7/ST0-ST7) sont conservés sur les commutateurs de contexte. Il n’existe pas de convention d’appel explicite pour ces registres. L’utilisation de ces registres est strictement interdite dans le code de mode noyau.

## <a name="fpcsr"></a>FpCsr

L’état du registre inclut également le mot de contrôle de l’UIP x87. La convention d’appel dicte que ce registre est nonvolatile.

Le registre des mots de contrôle FPU x87 est défini selon les valeurs standard suivantes au début de l’exécution du programme :

| Enregistrez les\[bits] | Paramètre |
|-|-|
| FPCSR\[0:6] | Masques d’exception tous les 1 (toutes les exceptions masquées) |
| FPCSR\[7] | Réservé - 0 |
| FPCSR\[8:9] | Contrôle de précision - 10B (double précision) |
| FPCSR\[10:11] | Contrôle d’arrondissement - 0 (rond au plus proche) |
| FPCSR\[12] | Contrôle de l’infini - 0 (non utilisé) |

Un callee qui modifie l’un des champs au sein de la FPCSR doit les restaurer avant de retourner à son appelant. En outre, un appelant qui a modifié l’un de ces champs doit les restaurer à leurs valeurs standard avant d’invoquer un appelant à moins que, par accord, le callee s’attende aux valeurs modifiées.

Il y a deux exceptions aux règles concernant la non-volatilité des indicateurs de contrôle :

1. Dans les fonctions où le but documenté de la fonction donnée est de modifier les drapeaux FpCsr nonvolatiles.

1. Lorsqu’il est manifestement exact que la violation de ces règles entraîne un programme qui se comporte de la même façon qu’un programme où ces règles ne sont pas violées, par exemple, par l’analyse de tout le programme.

## <a name="mxcsr"></a>MxCsr

L’état du registre comprend également MxCsr. La convention d’appel divise ce registre en une partie volatile et une partie non volatile. La partie volatile se compose des six drapeaux\[d’état, dans MXCSR 0:5], tandis que le reste du registre, MXCSR\[6:15], est considéré comme nonvolatile.

La partie non volatile est fixée aux valeurs standard suivantes au début de l’exécution du programme :

| Enregistrez les\[bits] | Paramètre |
|-|-|
| MXCSR\[6] | Les dénormes sont des zéros - 0 |
| MXCSR\[07:12] | Masques d’exception tous les 1 (toutes les exceptions masquées) |
| MXCSR\[13:14] | Contrôle d’arrondissement - 0 (rond au plus proche) |
| MXCSR\[15] | Flush à zéro pour le underflow masqué - 0 (off) |

Un callee qui modifie l’un des champs nonvolatiles dans MXCSR doit les restaurer avant de retourner à son appelant. En outre, un appelant qui a modifié l’un de ces champs doit les restaurer à leurs valeurs standard avant d’invoquer un appelant à moins que, par accord, le callee s’attende aux valeurs modifiées.

Il y a deux exceptions aux règles concernant la non-volatilité des indicateurs de contrôle :

- Dans les fonctions où le but documenté de la fonction donnée est de modifier les drapeaux MxCsr nonvolatiles.

- Lorsqu’il est manifestement exact que la violation de ces règles entraîne un programme qui se comporte de la même façon qu’un programme où ces règles ne sont pas violées, par exemple, par l’analyse de tout le programme.

Aucune hypothèse ne peut être faite au sujet de l’état de la partie volatile de MXCSR à travers une limite de fonction, à moins d’être décrite spécifiquement dans la documentation d’une fonction.

## <a name="setjmplongjmp"></a>setjmp/longjmp

Lorsque vous incluez setjmpex.h ou setjmp.h, tous les appels à [setjmp](../c-runtime-library/reference/setjmp.md) ou [longjmp](../c-runtime-library/reference/longjmp.md) aboutissent à un dénouement qui invoque destructeurs et `__finally` des appels.  Cela diffère de x86, où l’inclusion `__finally` de setjmp.h entraîne l’invoquation de clauses et de destructeurs.

Un appel `setjmp` pour préserver le pointeur de pile actuel, les registres non volatils et les registres MxCsr.  Appels `longjmp` à revenir au `setjmp` site d’appel le plus récent et réinitialise le pointeur de pile, les registres `setjmp` non volatils, et les registres MxCsr, de retour à l’état comme conservé par l’appel le plus récent.

## <a name="see-also"></a>Voir aussi

[Conventions des logiciels x64](../build/x64-software-conventions.md)
