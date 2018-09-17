---
title: seed_seq, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::seed_seq
- random/std::seed_seq::result_type
- random/std::seed_seq::generate
- random/std::seed_seq::size
- random/std::seed_seq::param
dev_langs:
- C++
helpviewer_keywords:
- std::seed_seq [C++]
- std::seed_seq [C++], result_type
- std::seed_seq [C++], generate
- std::seed_seq [C++], size
- std::seed_seq [C++], param
ms.assetid: cba114f7-9ac6-4f2f-b773-9c84805401d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2c4e86ff5ad4e1ebdba728202904324d9dc9e66f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711748"
---
# <a name="seedseq-class"></a>seed_seq, classe

Stocke un vecteur de valeurs entières non signées pouvant fournir une valeur initiale aléatoire pour un moteur de nombres aléatoires.

## <a name="syntax"></a>Syntaxe

```cpp
class seed_seq
   {
public:
   // types
   typedef unsigned int result_type;

   // constructors
   seed_seq();
   template <class T>
      seed_seq(initializer_list<T> initlist);
   template <class InputIterator>
      seed_seq(InputIterator begin, InputIterator end);

   // generating functions
   template <class RandomAccessIterator>
      void generate(RandomAccessIterator begin, RandomAccessIterator end);

   // property functions
   size_t size() const;
   template <class OutputIterator>
      void param(OutputIterator dest) const;

   // no copy functions
   seed_seq(const seed_seq&) = delete;
   void operator=(const seed_seq&) = delete;
   };
```

## <a name="types"></a>Types

```cpp
typedef unsigned int result_type;
```

Type des éléments de la séquence initiale. Type d’entier 32 bits non signé.

## <a name="constructors"></a>Constructeurs

```cpp
seed_seq();
```

Constructeur par défaut. Initialise la séquence pour obtenir une séquence interne vide.

```cpp
template<class T>
seed_seq(initializer_list<T> initlist);
```

Utilise `initlist` pour définir la séquence interne.
`T` doit être un type entier.

```cpp
template<class InputIterator>
seed_seq(InputIterator begin, InputIterator end);
```

Initialise la séquence interne à l'aide de tous les éléments de la plage d'itérateurs d'entrée fournie.
`iterator_traits<InputIterator>::value_type` doit être un type entier.

## <a name="members"></a>Membres

### <a name="generating-functions"></a>Fonctions de génération

```cpp
template<class RandomAccessIterator>
void generate(RandomAccessIterator begin,
          RandomAccessIterator end);
```

Remplit les éléments de la séquence fournie à l'aide d'un algorithme interne. Cet algorithme est affecté par la séquence interne avec laquelle `seed_seq` a été initialisé.
Rien ne se produit si `begin == end`.

### <a name="property-functions"></a>Fonctions de propriétés

```cpp
size_t size() const;
```

Retourne le nombre d'éléments d'un `seed_seq`.

```cpp
template<class OutputIterator>
void param(OutputIterator dest) const;
```

Copie la séquence interne dans l'itérateur de sortie `dest`.

## <a name="example"></a>Exemple

L'exemple de code suivant teste les trois constructeurs et génère une sortie à partir des instances `seed_seq` obtenues lors de l'assignation à un tableau. Pour obtenir un exemple qui utilise `seed_seq` avec un générateur de nombres aléatoires, consultez [\<random>](../standard-library/random.md).

```cpp
#include <iostream>
#include <random>
#include <string>
#include <array>

using namespace std;

void test(const seed_seq& sseq) {
    cout << endl << "seed_seq::size(): " << sseq.size() << endl;

    cout << "seed_seq::param(): ";
    ostream_iterator<unsigned int> out(cout, " ");
    sseq.param(out);
    cout << endl;

    cout << "Generating a sequence of 5 elements into an array: " << endl;
    array<unsigned int, 5> seq;
    sseq.generate(seq.begin(), seq.end());
    for (unsigned x : seq) { cout << x << endl; }
}

int main()
{
    seed_seq seed1;
    test(seed1);

    seed_seq seed2 = { 1701, 1729, 1791 };
    test(seed2);

    string sstr = "A B C D"; // seed string
    seed_seq seed3(sstr.begin(), sstr.end());
    test(seed3);
}
```

```Output
seed_seq::size(): 0
seed_seq::param():
Generating a sequence of 5 elements into an array:
505382999
163489202
3932644188
763126080
73937346

seed_seq::size(): 3
seed_seq::param(): 1701 1729 1791
Generating a sequence of 5 elements into an array:
1730669648
1954224479
2809786021
1172893117
2393473414

seed_seq::size(): 7
seed_seq::param(): 65 32 66 32 67 32 68
Generating a sequence of 5 elements into an array:
3139879222
3775111734
1084804564
2485037668
1985355432
```

## <a name="remarks"></a>Notes

Les fonctions membres de cette classe ne lèvent pas d’exceptions.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<random>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[\<random>](../standard-library/random.md)<br/>
