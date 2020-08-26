---
title: '&lt;chrono&gt;'
ms.date: 05/07/2019
f1_keywords:
- chrono/std::chrono::nanoseconds
- chrono/std::chrono::minutes
- chrono/std::chrono::seconds
- <chrono>
- chrono/std::chrono::hours
- chrono/std::chrono::milliseconds
- chrono/std::chrono::microseconds
ms.assetid: 844de749-f306-482e-89bc-6f53c99c8324
ms.openlocfilehash: b74c25e9c26d5767426576633e0999ae3ca44954
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840646"
---
# <a name="ltchronogt"></a>&lt;chrono&gt;

Incluez l’en-tête standard \<chrono> pour définir des classes et des fonctions qui représentent et manipulent des durées et des instants horaires.

À compter de Visual Studio 2015, l’implémentation de `steady_clock` a changé pour répondre aux exigences standard C++ pour en matière et monotonique. `steady_clock` est maintenant basé sur QueryPerformanceCounter() et `high_resolution_clock` est désormais un typedef pour `steady_clock`. Par conséquent, dans le compilateur Microsoft C++ `steady_clock::time_point` est désormais un typedef pour `chrono::time_point<steady_clock>` ; Toutefois, cette règle n’est pas nécessairement le cas pour d’autres implémentations.

## <a name="requirements"></a>Configuration requise

**En-tête :**\<chrono>

**Espace de noms :** std

## <a name="members"></a>Membres

### <a name="classes"></a>Classes

|Nom|Description|
|-|-|
|[Duration (classe)](../standard-library/duration-class.md)|Décrit un type qui contient un intervalle de temps.|
|[Classe time_point](../standard-library/time-point-class.md)|Décrit un type qui représente un point dans le temps.|

### <a name="structs"></a>Structures

|Nom|Description|
|-|-|
|[common_type, structure](../standard-library/common-type-structure.md)|Décrit les spécialisations du modèle de classe [common_type](../standard-library/common-type-class.md) pour les instanciations de `duration` et `time_point` .|
|[duration_values, structure](../standard-library/duration-values-structure.md)|Fournit des valeurs spécifiques pour le paramètre de modèle `duration``Rep`.|
|[struct high_resolution_clock](../standard-library/high-resolution-clock-struct.md)||
|[steady_clock, struct](../standard-library/steady-clock-struct.md)|Représente une horloge `steady`.|
|[system_clock, structure](../standard-library/system-clock-structure.md)|Représente un *type d’horloge* basé sur l’horloge en temps réel du système.|
|[treat_as_floating_point, structure](../standard-library/treat-as-floating-point-structure.md)|Spécifie si un type peut être traité comme un type à virgule flottante.|

### <a name="functions"></a>Functions

|Nom|Description|
|-|-|
|[duration_cast](../standard-library/chrono-functions.md#duration_cast)|Caste un objet `duration` en un type spécifié.|
|[time_point_cast](../standard-library/chrono-functions.md#time_point_cast)|Caste un objet `time_point` en un type spécifié.|

### <a name="operators"></a>Opérateurs

|Nom|Description|
|-|-|
|[and](../standard-library/chrono-operators.md#operator-)|Opérateur de soustraction ou de négation d'objets `duration` et `time_point`.|
|[opérateur ! =](../standard-library/chrono-operators.md#op_neq)|Opérateur d'inégalité utilisé avec des objets `duration` ou `time_point`.|
|[modulo, opérateur](../standard-library/chrono-operators.md#op_modulo)|Opérateur pour opérations de modulo sur des objets `duration`.|
|[and](../standard-library/chrono-operators.md#op_star)|Opérateur de multiplication pour les objets `duration`.|
|[and](../standard-library/chrono-operators.md#op_div)|Opérateur de division pour les objets `duration`.|
|[opérateur +](../standard-library/chrono-operators.md#op_add)|Ajoute des objets `duration` et `time_point`.|
|[and&lt;](../standard-library/chrono-operators.md#op_lt)|Détermine si un objet `duration` ou `time_point` est inférieur à un autre objet `duration` ou `time_point`.|
|[and&lt;=](../standard-library/chrono-operators.md#op_lt_eq)|Détermine si un objet `duration` ou `time_point` est inférieur ou égal à un autre objet `duration` ou `time_point`.|
|[opérateur = =](../standard-library/chrono-operators.md#op_eq_eq)|Détermine si deux objets `duration` représentent des intervalles de temps de même longueur ou si deux objets `time_point` représentent le même point dans le temps.|
|[and&gt;](../standard-library/chrono-operators.md#op_gt)|Détermine si un objet `duration` ou `time_point` est supérieur à un autre objet `duration` ou `time_point`.|
|[and&gt;=](../standard-library/chrono-operators.md#op_gt_eq)|Détermine si un objet `duration` ou `time_point` est supérieur ou égal à un autre objet `duration` ou `time_point`.|

### <a name="typedefs-predefined-duration-types"></a>Typedefs (types de durée prédéfinis)

Pour plus d’informations sur les types de rapports utilisés dans les typedefs suivants, consultez [\<ratio>](../standard-library/ratio.md) .

|Nom|Description|
|-|-|
|`typedef duration<long long, nano> nanoseconds;`|Synonyme pour un `duration` type qui a une période de cycle de 1 nanoseconde.|
|`typedef duration<long long, micro> microseconds;`|Synonyme pour un `duration` type qui a une période de cycle de 1 microseconde.|
|`typedef duration<long long, milli> milliseconds;`|Synonyme pour un `duration` type qui a une période de cycle de 1 milliseconde.|
|`typedef duration<long long> seconds;`|Synonyme pour un `duration` type qui a une période de cycle de 1 seconde.|
|`typedef duration<int, ratio<60> > minutes;`|Synonyme pour un `duration` type qui a une période de cycle de 1 minute.|
|`typedef duration<int, ratio<3600> > hours;`|Synonyme pour un `duration` type qui a une période de cycle de 1 heure.|

### <a name="literals"></a>Littéraux

**(C++ 11)** L' \<chrono> en-tête définit les [littéraux définis par l’utilisateur](../cpp/user-defined-literals-cpp.md) suivants que vous pouvez utiliser pour une plus grande commodité, la sécurité de type et la maintenabilité de votre code. Ces littéraux sont définis dans l'espace de noms inline `literals::chrono_literals` et sont dans la portée quand std::chrono est dans la portée.

|Déclaration|Description|
|-|-|
|`hours operator "" h(unsigned long long Val)`|Spécifie les heures comme valeur intégrale.|
|`duration<double, ratio<3600> > operator "" h(long double Val)`|Spécifie les heures comme valeur à virgule flottante.|
|`minutes (operator "" min)(unsigned long long Val)`|Spécifie les minutes comme valeur intégrale.|
|`duration<double, ratio<60> > (operator "" min)( long double Val)`|Spécifie les minutes comme valeur à virgule flottante.|
|`seconds operator "" s(unsigned long long Val)`|Spécifie les minutes comme valeur intégrale.|
|`duration<double> operator "" s(long double Val)`|Spécifie les secondes comme valeur à virgule flottante.|
|`milliseconds operator "" ms(unsigned long long Val)`|Spécifie les millisecondes comme valeur intégrale.|
|`duration<double, milli> operator "" ms(long double Val)`|Spécifie les millisecondes comme valeur à virgule flottante.|
|`microseconds operator "" us(unsigned long long Val)`|Spécifie les microsecondes comme valeur intégrale.|
|`duration<double, micro> operator "" us(long double Val)`|Spécifie les microsecondes comme valeur à virgule flottante.|
|`nanoseconds operator "" ns(unsigned long long Val)`|Spécifie les nanosecondes comme valeur intégrale.|
|`duration<double, nano> operator "" ns(long double Val)`|Spécifie les nanosecondes comme valeur à virgule flottante.|

Les exemples suivants montrent comment utiliser les littéraux chrono.

```cpp
constexpr auto day = 24h;
constexpr auto week = 24h* 7;
constexpr auto my_duration_unit = 108ms;
```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)
