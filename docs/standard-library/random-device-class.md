---
title: random_device, classe
ms.date: 11/04/2016
f1_keywords:
- random/std::random_device
- random/std::random_device::min
- random/std::random_device::max
- random/std::random_device::entropy
- random/std::random_device::operator()
helpviewer_keywords:
- std::random_device [C++]
- std::random_device [C++], min
- std::random_device [C++], max
- std::random_device [C++], entropy
- std::random_device [C++], entropy
ms.assetid: 4393d515-0cb6-4e0d-a2ba-c780f05dc1bf
ms.openlocfilehash: 783b8f587094c6d603cc02f41b516ebd7b1e9a08
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62369889"
---
# <a name="randomdevice-class"></a>random_device, classe

Génère une séquence aléatoire à partir d'un appareil externe.

## <a name="syntax"></a>Syntaxe

```cpp
class random_device {
public:
   typedef unsigned int result_type;

   // constructor
   explicit random_device(const std::string& token = "");

   // properties
   static result_type min();
   static result_type max();
   double entropy() const;

   // generate
   result_type operator()();

   // no-copy functions
   random_device(const random_device&) = delete;
   void operator=(const random_device&) = delete;
   };
```

## <a name="members"></a>Membres

|||
|-|-|
|[random_device](#random_device)|[entropy](#entropy)|
|[random_device::operator()](#op_call)||

## <a name="remarks"></a>Notes

La classe décrit une source de nombres aléatoires et a l'autorisation, sans y être obligée, d'être non déterministe ou sécurisée par chiffrement par la norme ISO C++. Dans l’implémentation Visual Studio, les valeurs produites sont non déterministes et sécurisées par chiffrement, mais elles sont exécutées plus lentement que les générateurs créés à partir de moteurs et d’adaptateurs de moteurs (tels que [mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md), le moteur rapide et très performant utilisé pour la plupart des applications).

Les résultats `random_device` sont distribués de manière uniforme dans la plage fermée [ `0, 2`<sup>32</sup>).

Il n'est pas garanti que `random_device` aboutisse à un appel non bloquant.

Généralement, `random_device` est utilisé pour amorcer d'autres générateurs créés avec des moteurs ou adaptateurs de moteurs. Pour plus d’informations, consultez [\<random>](../standard-library/random.md).

## <a name="example"></a>Exemple

Le code suivant illustre les fonctionnalités de base de cette classe et des exemples de résultats. En raison de la nature non déterministe de `random_device`, les valeurs aléatoires affichées dans la section **Sortie** ne correspondent pas à vos résultats. Cela est normal et prévu.

```cpp
// random_device_engine.cpp
// cl.exe /W4 /nologo /EHsc /MTd
#include <random>
#include <iostream>
using namespace std;

int main()
{
    random_device gen;

    cout << "entropy == " << gen.entropy() << endl;
    cout << "min == " << gen.min() << endl;
    cout << "max == " << gen.max() << endl;

    cout << "a random value == " << gen() << endl;
    cout << "a random value == " << gen() << endl;
    cout << "a random value == " << gen() << endl;
}
```

```Output
entropy == 32
min == 0
max == 4294967295
a random value == 2378414971
a random value == 3633694716
a random value == 213725214
```

Cet exemple est simpliste et ne représente pas le cas d'utilisation générale de ce générateur. Pour obtenir un exemple de code plus représentatif, consultez [\<random>](../standard-library/random.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** \<random>

**Espace de noms :** std

## <a name="random_device"></a>  random_device::random_device

Construit le générateur.

```cpp
random_device(const std::string& = "");
```

### <a name="remarks"></a>Notes

Le constructeur initialise le générateur si nécessaire, en ignorant le paramètre de chaîne. Lève une valeur d’un type défini par l’implémentation dérivé d’[exception](../standard-library/exception-class.md) si `random_device` n’a pas pu être initialisé.

## <a name="entropy"></a>  random_device::entropy

Estime le caractère aléatoire de la source.

```cpp
double entropy() const noexcept;
```

### <a name="remarks"></a>Notes

La fonction membre retourne une estimation du caractère aléatoire de la source, exprimée en bits.

## <a name="op_call"></a>  random_device::operator()

Retourne une valeur aléatoire.

```cpp
result_type operator()();
```

### <a name="remarks"></a>Notes

Retourne des valeurs distribuées uniformément dans l’intervalle fermé [`min, max`] comme déterminé par les fonctions membres `min()` et `max()`. Lève une valeur d’un type défini par l’implémentation dérivé d’[exception](../standard-library/exception-class.md) si un nombre aléatoire n’a pas pu être obtenu.

## <a name="see-also"></a>Voir aussi

[\<random>](../standard-library/random.md)<br/>
