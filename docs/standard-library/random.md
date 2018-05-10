---
title: '&lt;random&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 08/24/2017
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <random>
dev_langs:
- C++
helpviewer_keywords:
- random header
ms.assetid: 60afc25c-b162-4811-97c1-1b65398d4c57
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bdfae58c03d18638ad44f844909d585b41d710cd
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
---
# <a name="ltrandomgt"></a>&lt;random&gt;

Définit des fonctions pour la génération de nombres aléatoires, ce qui permet la création de nombres aléatoires distribués de manière uniforme.

## <a name="syntax"></a>Syntaxe

```cpp
#include <random>
```

## <a name="summary"></a>Récapitulatif

Un *générateur de nombres aléatoires* est un objet qui produit une séquence de valeurs pseudo-aléatoires. Un générateur qui produit des valeurs distribuées de manière uniforme dans une plage spécifiée est un *générateur de nombres aléatoires uniformes* (URNG). Une classe de modèle conçue pour fonctionner comme un générateur URNG est appelée *moteur* si elle a certaines caractéristiques communes, qui sont présentées plus loin dans cet article. Un générateur URNG peut être (et est généralement) combiné avec une *distribution* en passant le générateur URNG comme argument à l’élément `operator()` de la distribution pour produire les valeurs qui sont distribuées comme le définit la distribution.

Ces liens permettent d'accéder aux principales sections de cet article :

- [Exemples](#code)

- [Liste par catégorie](#listing)

- [Moteurs et distributions](#engdist)

- [Notes](#comments)

### <a name="quick-tips"></a>Conseils rapides

Voici quelques conseils à prendre en compte lors de l’utilisation \<aléatoire > :

- Dans la plupart des cas, les générateurs URNG produisent des bits bruts qui doivent être mis en forme par les distributions. ([std::shuffle()](../standard-library/algorithm-functions.md#shuffle) est une exception notable, car il utilise directement un générateur URNG.)

- Une seule instanciation d'un générateur URNG ou d'une distribution ne peut pas être appelée en toute sécurité simultanément, car l'exécution d'un générateur URNG ou d'une distribution est une opération de modification. Pour plus d’informations, consultez [Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md).

- Les [typedefs prédéfinis](#typedefs) de plusieurs moteurs sont fournis. Il s’agit du mode de création recommandé pour créer un générateur URNG si un moteur est utilisé.

- Pour la plupart des applications, l’association la plus utile est le moteur `mt19937` avec `uniform_int_distribution`, comme illustré dans l’[exemple de code](#code) plus loin dans cet article.

Il existe plusieurs options permettant de choisir dans le \<aléatoire > en-tête et que l’un d’eux est préférable à la fonction C Runtime obsolète `rand()`. Pour plus d’informations sur les problèmes avec `rand()` et comment \<aléatoire > les traite, consultez [cette vidéo](http://go.microsoft.com/fwlink/p/?linkid=397615).

## <a name="code"></a> Exemples

L'exemple de code suivant montre comment générer des nombres aléatoires. Dans le cas présent, cinq d'entre eux utilisent un générateur créé avec une valeur initiale non déterministe.

```cpp
#include <random>
#include <iostream>

using namespace std;

int main()
{
    random_device rd;   // non-deterministic generator
    mt19937 gen(rd());  // to seed mersenne twister.
                        // replace the call to rd() with a
                        // constant value to get repeatable
                        // results.

    for (int i = 0; i < 5; ++i) {
        cout << gen() << " "; // print the raw output of the generator.
    }
    cout << endl;
}
```

```Output
2430338871 3531691818 2723770500 3252414483 3632920437
```

Bien qu'il s'agisse de nombres aléatoires de haute qualité, différents à chaque exécution de ce programme, ils ne sont pas nécessairement dans une plage utile. Pour contrôler la plage, utilisez une distribution uniforme, comme illustré dans le code suivant :

```cpp
#include <random>
#include <iostream>

using namespace std;

int main()
{
    random_device rd;   // non-deterministic generator
    mt19937 gen(rd());  // to seed mersenne twister.
    uniform_int_distribution<> dist(1,6); // distribute results between 1 and 6 inclusive.

    for (int i = 0; i < 5; ++i) {
        cout << dist(gen) << " "; // pass the generator to the distribution.
    }
    cout << endl;
}
```

```Output
5 1 6 1 2
```

L'exemple de code suivant illustre un ensemble de cas d'usage plus réaliste avec des générateurs de nombres aléatoires distribués de manière uniforme. Ces derniers lisent de façon aléatoire le contenu d'un vecteur et d'un tableau.

```cpp
// cl.exe /EHsc /nologo /W4 /MTd
#include <algorithm>
#include <array>
#include <iostream>
#include <random>
#include <string>
#include <vector>
#include <functional> // ref()

using namespace std;

template <typename C> void print(const C& c) {
    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

template <class URNG>
void test(URNG& urng) {

    // Uniform distribution used with a vector
    // Distribution is [-5, 5] inclusive
    uniform_int_distribution<int> dist(-5, 5);
    vector<int> v;

    for (int i = 0; i < 20; ++i) {
        v.push_back(dist(urng));
    }

    cout << "Randomized vector: ";
    print(v);

    // Shuffle an array
    // (Notice that shuffle() takes a URNG, not a distribution)
    array<string, 26> arr = { { "H", "He", "Li", "Be", "B", "C", "N", "O", "F",
        "Ne", "Na", "Mg", "Al", "Si", "P", "S", "Cl", "Ar", "K", "Ca", "Sc",
        "Ti", "V", "Cr", "Mn", "Fe" } };

    shuffle(arr.begin(), arr.end(), urng);

    cout << "Randomized array: ";
    print(arr);
    cout << "--" << endl;
}

int main()
{
    // First run: non-seedable, non-deterministic URNG random_device
    // Slower but crypto-secure and non-repeatable.
    random_device rd;
    cout << "Using random_device URNG:" << endl;
    test(rd);

    // Second run: simple integer seed, repeatable results
    cout << "Using constant-seed mersenne twister URNG:" << endl;
    mt19937 engine1(12345);
    test(engine1);

    // Third run: random_device as a seed, different each run
    // (Desirable for most purposes)
    cout << "Using non-deterministic-seed mersenne twister URNG:" << endl;
    mt19937 engine2(rd());
    test(engine2);

    // Fourth run: "warm-up" sequence as a seed, different each run
    // (Advanced uses, allows more than 32 bits of randomness)
    cout << "Using non-deterministic-seed \"warm-up\" sequence mersenne twister URNG:" << endl;
    array<unsigned int, mt19937::state_size> seed_data;
    generate_n(seed_data.begin(), seed_data.size(), ref(rd));
    seed_seq seq(begin(seed_data), end(seed_data));
    mt19937 engine3(seq);
    test(engine3);
}
```

```Output
Using random_device URNG:
Randomized vector: 5 -4 2 3 0 5 -2 0 4 2 -1 2 -4 -3 1 4 4 1 2 -2
Randomized array: O Li V K C Ti N Mg Ne Sc Cl B Cr Mn Ca Al F P Na Be Si Ar Fe S He H
--
Using constant-seed mersenne twister URNG:
Randomized vector: 3 -1 -5 0 0 5 3 -4 -3 -4 1 -3 0 -3 -2 -4 5 1 -1 -1
Randomized array: Al O Ne Si Na Be C N Cr Mn H V F Sc Mg Fe K Ca S Ti B P Ar Cl Li He
--
Using non-deterministic-seed mersenne twister URNG:
Randomized vector: 5 -4 0 2 1 -2 4 4 -4 0 0 4 -5 4 -5 -1 -3 0 0 3
Randomized array: Si Fe Al Ar Na P B Sc H F Mg Li C Ti He N Mn Be O Ca Cr V K Ne Cl S
--
Using non-deterministic-seed "warm-up" sequence mersenne twister URNG:
Randomized vector: -1 3 -2 4 1 3 0 -5 5 -5 0 0 5 0 -3 3 -4 2 5 0
Randomized array: Si C Sc H Na O S Cr K Li Al Ti Cl B Mn He Fe Ne Be Ar V P Ca N Mg F
--
```

Ce code illustre deux randomisations différentes (rendre aléatoire un vecteur d'entiers et lire de façon aléatoire un tableau de données indexées) avec une fonction avec modèle de test. Le premier appel à la fonction de test utilise le générateur URNG sécurisé par chiffrement, non déterministe, sans valeur initiale et non renouvelable `random_device`. La deuxième série de tests utilise `mersenne_twister_engine` comme générateur URNG, avec une valeur initiale constante 32 bits déterministe, ce qui signifie que les résultats sont renouvelables. La troisième série de tests amorce `mersenne_twister_engine` avec un résultat non déterministe 32 bits de `random_device`. La quatrième série de tests poursuit ce développement en utilisant une [séquence de valeurs initiales](../standard-library/seed-seq-class.md) remplie avec des résultats `random_device`, qui présente de manière effective un caractère aléatoire non déterministe de plus de 32 bits (mais toujours pas sécurisé par chiffrement). Pour plus d'informations, lisez la suite.

## <a name="listing"></a> Liste par catégorie

###  <a name="urngs"></a> Générateurs de nombres aléatoires uniformes

Les générateurs URNG sont souvent décrits sous l'angle des propriétés suivantes :

1. **Longueur de période** : nombre d’itérations nécessaires pour répéter la séquence des nombres générés. Plus la période est longue, mieux c'est.

2. **Performances** : vitesse à laquelle les nombres peuvent être générés et quantité de mémoire nécessaire. Plus la valeur est faible, mieux c'est.

3. **Qualité** : proximité de la séquence générée des nombres véritablement aléatoires. Cette propriété est souvent appelée *caractère aléatoire*.

Les sections suivantes répertorient les générateurs (générateurs Urng) fournis dans le \<aléatoire > en-tête.

####  <a name="rd"></a> Générateur non déterministe

|||
|-|-|
|[random_device, classe](../standard-library/random-device-class.md)|Génère une séquence aléatoire non déterministe, sécurisée par chiffrement à l'aide d'un appareil externe. Généralement utilisé pour amorcer un moteur. Performances faibles, très haute qualité. Pour plus d’informations, consultez [Notes](#comments).|

####  <a name="typedefs"></a> Typedefs de moteur avec paramètres prédéfinis

Pour l'instanciation des moteurs et adaptateurs de moteurs. Pour plus d’informations, consultez [Moteurs et distributions](#engdist).

- `default_random_engine` : moteur par défaut.
 `typedef mt19937 default_random_engine;`

- `knuth_b` : moteur Knuth.
 `typedef shuffle_order_engine<minstd_rand0, 256> knuth_b;`

- `minstd_rand0` : moteur standard minimal 1988 (Lewis, Goodman et Miller, 1969).
 `typedef linear_congruential_engine<unsigned int, 16807, 0, 2147483647> minstd_rand0;`

- `minstd_rand` : moteur standard minimal mis à jour `minstd_rand0` (Park, Miller et Stockmeyer, 1993).
 `typedef linear_congruential_engine<unsigned int, 48271, 0, 2147483647> minstd_rand;`

- `mt19937` : moteur twister Mersenne 32 bits (Matsumoto et Nishimura, 1998).
 `typedef mersenne_twister_engine<unsigned int, 32, 624, 397,      31, 0x9908b0df,      11, 0xffffffff,      7, 0x9d2c5680,      15, 0xefc60000,      18, 1812433253> mt19937;`

- `mt19937_64` : moteur twister Mersenne 64 bits (Matsumoto et Nishimura, 2000).
 `typedef mersenne_twister_engine<unsigned long long, 64, 312, 156,      31, 0xb5026f5aa96619e9ULL,      29, 0x5555555555555555ULL,      17, 0x71d67fffeda60000ULL,      37, 0xfff7eee000000000ULL,      43, 6364136223846793005ULL> mt19937_64;`

- `ranlux24` moteur RANLUX 24 bits (Martin Lüscher et Fred James, 1994).
 `typedef discard_block_engine<ranlux24_base, 223, 23> ranlux24;`

- `ranlux24_base` : utilisé comme base pour `ranlux24`.
 `typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;`

- `ranlux48` moteur RANLUX 48 bits (Martin Lüscher et Fred James, 1994).
 `typedef discard_block_engine<ranlux48_base, 389, 11> ranlux48;`

- `ranlux48_base` : utilisé comme base pour `ranlux48`.
 `typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;`

####  <a name="eng"></a> Modèles de moteurs

Les modèles de moteurs sont utilisés comme générateurs URNG autonomes ou comme moteurs de base passés aux [adaptateurs de moteurs](#engadapt). En général, ils sont instanciés avec un [typedef de moteur prédéfini](#typedefs) et passés à une [distribution](#distributions). Pour plus d’informations, consultez la section [Moteurs et distributions](#engdist).

|||
|-|-|
|[linear_congruential_engine, classe](../standard-library/linear-congruential-engine-class.md)|Génère une séquence aléatoire en utilisant l'algorithme congruentiel linéaire. Moteur le plus simple avec la qualité la plus basse.|
|[mersenne_twister_engine, classe](../standard-library/mersenne-twister-engine-class.md)|Génère une séquence aléatoire en utilisant l'algorithme twister de Mersenne. Moteur le plus complexe avec la qualité la plus élevée, à l'exception de la classe random_device. Performances très élevées.|
|[subtract_with_carry_engine, classe](../standard-library/subtract-with-carry-engine-class.md)|Génère une séquence aléatoire en utilisant l'algorithme SWC (Substract With Carry). Version améliorée de `linear_congruential_engine`, mais avec des performances et une qualité beaucoup plus faibles que `mersenne_twister_engine`.|

####  <a name="engadapt"></a> Modèles d’adaptateurs de moteurs

Les adaptateurs de moteurs sont des modèles qui adaptent d'autres moteurs (de base). En général, ils sont instanciés avec un [typedef de moteur prédéfini](#typedefs) et passés à une [distribution](#distributions). Pour plus d’informations, consultez la section [Moteurs et distributions](#engdist).

|||
|-|-|
|[discard_block_engine, classe](../standard-library/discard-block-engine-class.md)|Génère une séquence aléatoire en ignorant les valeurs retournées par son moteur de base.|
|[independent_bits_engine, classe](../standard-library/independent-bits-engine-class.md)|Génère une séquence aléatoire avec un nombre spécifié de bits en recompressant les bits des valeurs retournées par son moteur de base.|
|[shuffle_order_engine, classe](../standard-library/shuffle-order-engine-class.md)|Génère une séquence aléatoire en réordonnançant les valeurs retournées à partir de son moteur de base.|

[[Modèles de moteurs](#eng)]

###  <a name="distributions"></a> Distributions de nombres aléatoires

Les sections suivantes répertorient les distributions fournies dans le \<aléatoire > en-tête. Les distributions sont un mécanisme de post-traitement qui utilise généralement la sortie de générateur URNG comme entrée et distribue la sortie selon une fonction de densité de probabilité statistique définie. Pour plus d’informations, consultez la section [Moteurs et distributions](#engdist).

#### <a name="uniform-distributions"></a>Distributions uniformes

|||
|-|-|
|[uniform_int_distribution, classe](../standard-library/uniform-int-distribution-class.md)|Produit une distribution de valeurs entières uniforme dans une plage de l’intervalle fermé \[a, b] (inclusive-inclusive).|
|[uniform_real_distribution, classe](../standard-library/uniform-real-distribution-class.md)|Produit une distribution de valeurs (à virgule flottante) réelles uniforme dans une plage de l’intervalle demi-ouvert [a, b) (inclusive-exclusive).|
|[generate_canonical](../standard-library/random-functions.md#generate_canonical)|Produit une distribution égale de valeurs (à virgule flottante) réelles d'une précision donnée dans [0, 1) (inclusive - exclusive).|

[[Distributions de nombres aléatoires](#distributions)]

#### <a name="bernoulli-distributions"></a>Distributions de Bernoulli

|||
|-|-|
|[bernoulli_distribution, classe](../standard-library/bernoulli-distribution-class.md)|Produit une distribution de Bernoulli de valeurs `bool`.|
|[binomial_distribution, classe](../standard-library/binomial-distribution-class.md)|Produit une distribution binomiale de valeurs entières.|
|[geometric_distribution, classe](../standard-library/geometric-distribution-class.md)|Produit une distribution géométrique de valeurs entières.|
|[negative_binomial_distribution, classe](../standard-library/negative-binomial-distribution-class.md)|Produit une distribution négative binomiale de valeurs entières.|

[[Distributions de nombres aléatoires](#distributions)]

#### <a name="normal-distributions"></a>Distributions normales

|||
|-|-|
|[cauchy_distribution, classe](../standard-library/cauchy-distribution-class.md)|Produit une distribution suivant une loi de Cauchy de valeurs (à virgule flottante) réelles.|
|[chi_squared_distribution, classe](../standard-library/chi-squared-distribution-class.md)|Produit une distribution suivant la loi unilatérale du Khi-deux de valeurs (à virgule flottante) réelles.|
|[fisher_f_distribution, classe](../standard-library/fisher-f-distribution-class.md)|Produit une distribution F (également appelée distribution de F de Snedecor ou la distribution de Fisher-Snedecor) de valeurs réelles (à virgule flottante).|
|[lognormal_distribution, classe](../standard-library/lognormal-distribution-class.md)|Produit une distribution suivant une loi log-normale de valeurs (à virgule flottante) réelles.|
|[normal_distribution, classe](../standard-library/normal-distribution-class.md)|Produit une distribution normale (loi gaussienne) de valeurs (à virgule flottante) réelles.|
|[student_t_distribution, classe](../standard-library/student-t-distribution-class.md)|Produit une distribution de valeurs à virgule flottante réelles suivant une loi *T* de Student.|

[[Distributions de nombres aléatoires](#distributions)]

#### <a name="poisson-distributions"></a>Probabilités de variables aléatoires suivant une loi de Poisson

|||
|-|-|
|[exponential_distribution, classe](../standard-library/exponential-distribution-class.md)|Produit une distribution exponentielle de valeurs (à virgule flottante) réelles.|
|[extreme_value_distribution, classe](../standard-library/extreme-value-distribution-class.md)|Produit une distribution suivant la loi d'extremum de valeurs (à virgule flottante) réelles.|
|[gamma_distribution, classe](../standard-library/gamma-distribution-class.md)|Produit une distribution Gamma de valeurs (à virgule flottante) réelles.|
|[poisson_distribution, classe](../standard-library/poisson-distribution-class.md)|Produit une probabilité d'une variable aléatoire suivant une loi de Poisson de valeurs entières.|
|[weibull_distribution, classe](../standard-library/weibull-distribution-class.md)|Produit une distribution de Weibull de valeurs (à virgule flottante) réelles.|

[[Distributions de nombres aléatoires](#distributions)]

#### <a name="sampling-distributions"></a>Distributions d'échantillonnages

|||
|-|-|
|[discrete_distribution, classe](../standard-library/discrete-distribution-class.md)|Produit une distribution d'entiers discrète.|
|[piecewise_constant_distribution, classe](../standard-library/piecewise-constant-distribution-class.md)|Produit une distribution constante par morceaux de valeurs (à virgule flottante) réelles.|
|[piecewise_linear_distribution, classe](../standard-library/piecewise-linear-distribution-class.md)|Produit une distribution linéaire par morceaux de valeurs (à virgule flottante) réelles.|

[[Distributions de nombres aléatoires](#distributions)]

### <a name="utility-functions"></a>Fonctions utilitaires

Cette section répertorie les fonctions utilitaires générales fournies dans le \<aléatoire > en-tête.

|||
|-|-|
|[seed_seq, classe](../standard-library/seed-seq-class.md)|Génère une séquence de valeurs initiales brouillée non tronquée. Utilisée pour éviter la réplication de flux de variantes aléatoires. Utile quand de nombreux générateurs URNG sont instanciés à partir de moteurs.|

### <a name="operators"></a>Opérateurs

Cette section répertorie les opérateurs fournis dans le \<aléatoire > en-tête.

|||
|-|-|
|`operator==`|Teste si le générateur URNG situé à gauche de l'opérateur est égal au moteur situé à droite.|
|`operator!=`|Teste si le générateur URNG situé à gauche de l'opérateur n'est pas égal au moteur situé à droite.|
|`operator<<`|Écrit des informations d'état dans un flux.|
|`operator>>`|Extrait des informations d'état d'un flux.|

## <a name="engdist"></a> Moteurs et distributions

Reportez-vous aux sections suivantes pour plus d’informations sur chacune de ces catégories de classe de modèle définis dans \<aléatoire >. Ces deux catégories de classes de modèles acceptent un type comme argument et utilisent des noms de paramètres de modèles partagés pour décrire les propriétés du type qui sont autorisées en tant que type d'argument réel, comme suit :

- `IntType` indique un `short`, `int`, `long`, `long long`, `unsigned short`, `unsigned int`, `unsigned long` ou `unsigned long long`.

- `UIntType` indique `unsigned short`, `unsigned int`, `unsigned long` ou `unsigned long long`.

- `RealType` indique un `float`, `double` ou `long double`.

### <a name="engines"></a>Moteurs

Les [modèles de moteurs](#eng) et les [modèles d’adaptateurs de moteurs](#engadapt) sont des modèles dont les paramètres personnalisent le générateur créé.

Un *moteur* est une classe ou une classe de modèle dont les instances (générateurs) agissent comme source de nombres aléatoires distribués de manière uniforme entre une valeur minimale et une valeur maximale. Un *adaptateur de moteur* fournit une séquence de valeurs qui ont différentes propriétés de caractère aléatoire en acceptant des valeurs produites par un autre moteur de nombres aléatoires et en appliquant un algorithme d’un certain genre à ces valeurs.

Chaque moteur et chaque adaptateur de moteur possèdent les membres suivants :

- `typedef` `numeric-type` `result_type` est le type retourné par l’élément `operator()` du générateur. Le `numeric-type` est passé en tant que paramètre de modèle lors de l'instanciation.

- `result_type operator()` retourne des valeurs qui sont distribuées de manière uniforme entre `min()` et `max()`.

- `result_type min()` retourne la valeur minimale retournée par l'élément `operator()` du générateur. Les adaptateurs de moteurs utilisent le résultat `min()` du moteur de base.

- `result_type max()` retourne la valeur maximale retournée par l'élément `operator()` du générateur. Quand `result_type` est un type intégral (à valeur entière), `max()` est la valeur maximale qui peut être retournée (valeur comprise) ; quand `result_type` est un type à virgule flottante (à valeur réelle), `max()` est la plus petite valeur supérieure à toutes les valeurs qui peut être retournée (valeur non comprise). Les adaptateurs de moteurs utilisent le résultat `max()` du moteur de base.

- `void seed(result_type s)` amorce le générateur avec la valeur initiale `s`. Pour les moteurs, la signature est `void seed(result_type s = default_seed)` pour une prise en charge des paramètres par défaut (les adaptateurs de moteurs définissent une valeur `void seed()` distincte, consultez la sous-section suivante).

- `template <class Seq> void seed(Seq& q)` amorce le générateur avec une classe [seed_seq](../standard-library/seed-seq-class.md)`Seq`.

- Constructeur explicite avec argument `result_type x` qui crée un générateur amorcé comme par un appel à `seed(x)`.

- Constructeur explicite avec argument `seed_seq& seq` qui crée un générateur amorcé comme par un appel à `seed(seq)`.

- `void discard(unsigned long long count)` appelle en fait `operator()` `count` fois et ignore chaque valeur.

En outre, les **adaptateurs de moteurs** prennent en charge ces membres (`Engine` est le premier paramètre de modèle d’un adaptateur de moteur, désignant le type de moteur de base) :

- Constructeur par défaut pour initialiser le générateur comme depuis le constructeur par défaut du moteur de base.

- Constructeur explicite avec argument `const Engine& eng`. Le but est de prendre en charge la construction de copie à l'aide du moteur de base.

- Constructeur explicite avec argument `Engine&& eng`. Le but est de prendre en charge la construction de déplacement à l'aide du moteur de base.

- `void seed()` qui initialise le générateur avec la valeur initiale par défaut du moteur de base.

- Fonction de propriété `const Engine& base()` qui retourne le moteur de base utilisé pour construire le générateur.

Chaque moteur tient à jour un *état* qui détermine la séquence de valeurs qui sera générée par les appels suivants à `operator()`. Les états de deux générateurs instanciés à partir de moteurs du même type peuvent être comparés en utilisant `operator==` et `operator!=`. Si les deux états sont égaux, ils génèrent la même séquence de valeurs. L'état d'un objet peut être enregistré dans un flux comme une séquence de valeurs non signés 32 bits en utilisant l'élément `operator<<` du générateur. L'état n'est pas modifié quand il est enregistré. Un état enregistré peut être lu dans un générateur instancié à partir d'un moteur du même type avec `operator>>`.

### <a name="distributions"></a>Distributions

Une [distribution de nombres aléatoires](#distributions) est une classe ou une classe de modèle dont les instances transforment un flux de nombres aléatoires distribués de manière uniforme obtenus à partir d’un moteur en un flux de nombres aléatoires qui ont une distribution particulière. Chaque distribution possède les membres suivants :

- `typedef` `numeric-type` `result_type` est le type retourné par l’élément `operator()` de la distribution. Le `numeric-type` est passé en tant que paramètre de modèle lors de l'instanciation.

- `template <class URNG> result_type operator()(URNG& gen)` retourne des valeurs distribuées en fonction de la définition de la distribution, en utilisant `gen` comme une source de valeurs aléatoires distribuées de manière uniforme et les *paramètres stockés de la distribution*.

- `template <class URNG> result_type operator()(URNG& gen, param_type p)` retourne des valeurs distribuées en fonction de la définition de la distribution, en utilisant `gen` comme une source de valeurs aléatoires distribuées de manière uniforme et la structure des paramètres `p`.

- `typedef` `unspecified-type` `param_type` est le package de paramètres éventuellement passé à `operator()`. Il est utilisé à la place des paramètres stockés pour générer sa valeur de retour.

- Un constructeur `const param&` initialise les paramètres stockés à partir de son argument.

- `param_type param() const` obtient les paramètres stockés.

- `void param(const param_type&)` définit les paramètres stockés à partir de son argument.

- `result_type min()` retourne la valeur minimale retournée par l'élément `operator()` de la distribution.

- `result_type max()` retourne la valeur maximale retournée par l'élément `operator()` de la distribution. Quand `result_type` est un type intégral (à valeur entière), `max()` est la valeur maximale qui peut être retournée (valeur comprise) ; quand `result_type` est un type à virgule flottante (à valeur réelle), `max()` est la plus petite valeur supérieure à toutes les valeurs qui peut être retournée (valeur non comprise).

- `void reset()` ignore toutes les valeurs mises en cache, afin que le résultat de l'appel suivant à `operator()` ne dépende d'aucune valeur obtenue à partir du moteur avant l'appel.

Une structure de paramètre est un objet qui stocke tous les paramètres nécessaires pour une distribution. Elle contient :

- `typedef` `distribution-type` `distribution_type`, qui est le type de sa distribution.

- Un ou plusieurs constructeurs qui acceptent les mêmes listes de paramètres que les constructeurs de distribution.

- Les mêmes fonctions d'accès aux paramètres que la distribution.

- Des opérateurs de comparaison d'égalité et d'inégalité.

Pour plus d'informations, consultez les sous-rubriques de référence sous celle-ci, liées précédemment dans cet article.

## <a name="comments"></a> Notes

Il existe deux générateurs URNG très utiles dans Visual Studio, `mt19937` et `random_device`, comme illustré dans cette table de comparaison :

|Générateur URNG|Rapide|Sécurisé par chiffrement|Avec valeur initiale|Déterministe|
|----------|-----------|---------------------|---------------|--------------------|
|`mt19937`|Oui|Non|Oui|Oui<sup>*</sup>|
|`random_device`|Non|Oui|Non|Non|

<sup>* Quand il est fourni avec une valeur initiale connue.</sup>

Même si la norme ISO C++ n'exige pas que `random_device` soit sécurisé par chiffrement, il est implémenté dans Visual Studio pour être sécurisé par chiffrement. (Le terme « sécurisé par chiffrement » n'implique pas de garanties, mais fait référence à un niveau minimal d'entropie (et donc au niveau de prévisibilité) fourni par un algorithme de randomisation donné. Pour plus d’informations, consultez l’article de Wikipedia [Cryptographically secure pseudorandom number generator](http://go.microsoft.com/fwlink/p/?linkid=398017).) Comme la norme ISO C++ n'a pas cette exigence, d'autres plateformes peuvent implémenter `random_device` comme un générateur de nombres pseudo-aléatoires simple (non sécurisé par chiffrement) et n'être appropriées que comme source de valeurs initiales pour un autre générateur. Recherchez ces plateformes dans la documentation quand vous utilisez `random_device` dans du code entre plateformes.

Par définition, les résultats `random_device` ne peuvent pas être reproduits et un effet secondaire est que son exécution peut être beaucoup plus lente que celle d'autres générateurs URNG. La plupart des applications qui ne sont pas tenues d’être sécurisées par chiffrement utilisent `mt19937` ou un moteur semblable, même si vous pouvez être amené à l’amorcer avec un appel à `random_device`, comme illustré dans l’[exemple de code](#code).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
