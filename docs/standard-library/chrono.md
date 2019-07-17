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
ms.openlocfilehash: 72d16b068f337fe935d07e1eb2d0e2b74de6268f
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244865"
---
# <a name="ltchronogt"></a>&lt;chrono&gt;

Incluez l’en-tête standard \<chrono> pour définir des classes et des fonctions qui représentent et manipulent des durées et des instants.

À compter de Visual Studio 2015, l’implémentation de `steady_clock` a changé pour satisfaire les exigences de la norme C++ en matière de stabilité et d’unitonicité. `steady_clock` est maintenant basé sur QueryPerformanceCounter() et `high_resolution_clock` est désormais un typedef pour `steady_clock`. Par conséquent, dans le Microsoft C++ compilateur `steady_clock::time_point` est désormais un typedef pour `chrono::time_point<steady_clock>`; Toutefois, cette règle n’est pas nécessairement le cas pour d’autres implémentations.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<chrono >

**Espace de noms :** std

## <a name="members"></a>Membres

### <a name="classes"></a>Classes

|||
|-|-|
|[duration, classe](../standard-library/duration-class.md)|Décrit un type qui contient un intervalle de temps.|
|[time_point, classe](../standard-library/time-point-class.md)|Décrit un type qui représente un point dans le temps.|

### <a name="structs"></a>Structs

|||
|-|-|
|[common_type, structure](../standard-library/common-type-structure.md)|Décrit les spécialisations de la classe de modèle [common_type](../standard-library/common-type-class.md) pour les instanciations de `duration` et `time_point`.|
|[duration_values, structure](../standard-library/duration-values-structure.md)|Fournit des valeurs spécifiques pour le paramètre de modèle `duration` `Rep`.|
|[high_resolution_clock struct](../standard-library/high-resolution-clock-struct.md)||
|[steady_clock, struct](../standard-library/steady-clock-struct.md)|Représente une horloge `steady`.|
|[system_clock, structure](../standard-library/system-clock-structure.md)|Représente un *type d’horloge* basé sur l’horloge en temps réel du système.|
|[treat_as_floating_point, structure](../standard-library/treat-as-floating-point-structure.md)|Spécifie si un type peut être traité comme un type à virgule flottante.|

### <a name="functions"></a>Fonctions

|||
|-|-|
|[duration_cast](../standard-library/chrono-functions.md#duration_cast)|Caste un objet `duration` en un type spécifié.|
|[time_point_cast](../standard-library/chrono-functions.md#time_point_cast)|Caste un objet `time_point` en un type spécifié.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[operator-](../standard-library/chrono-operators.md#operator-)|Opérateur de soustraction ou de négation d'objets `duration` et `time_point`.|
|[!=, opérateur](../standard-library/chrono-operators.md#op_neq)|Opérateur d'inégalité utilisé avec des objets `duration` ou `time_point`.|
|[opérateur modulo](../standard-library/chrono-operators.md#op_modulo)|Opérateur pour opérations de modulo sur des objets `duration`.|
|[operator*](../standard-library/chrono-operators.md#op_star)|Opérateur de multiplication pour les objets `duration`.|
|[operator/](../standard-library/chrono-operators.md#op_div)|Opérateur de division pour les objets `duration`.|
|[operator+](../standard-library/chrono-operators.md#op_add)|Ajoute des objets `duration` et `time_point`.|
|[operator&lt;](../standard-library/chrono-operators.md#op_lt)|Détermine si un objet `duration` ou `time_point` est inférieur à un autre objet `duration` ou `time_point`.|
|[operator&lt;=](../standard-library/chrono-operators.md#op_lt_eq)|Détermine si un objet `duration` ou `time_point` est inférieur ou égal à un autre objet `duration` ou `time_point`.|
|[operator==](../standard-library/chrono-operators.md#op_eq_eq)|Détermine si deux objets `duration` représentent des intervalles de temps de même longueur ou si deux objets `time_point` représentent le même point dans le temps.|
|[operator&gt;](../standard-library/chrono-operators.md#op_gt)|Détermine si un objet `duration` ou `time_point` est supérieur à un autre objet `duration` ou `time_point`.|
|[operator&gt;=](../standard-library/chrono-operators.md#op_gt_eq)|Détermine si un objet `duration` ou `time_point` est supérieur ou égal à un autre objet `duration` ou `time_point`.|

### <a name="typedefs-predefined-duration-types"></a>Typedefs (Types de durée prédéfinis)

Pour plus d’informations sur les types de rapports utilisés dans les typedefs suivants, consultez [\<ratio>](../standard-library/ratio.md).

||| ||| | `typedef duration<long long, nano> nanoseconds;`| Synonyme pour un `duration` type qui a un cycle de 1 nanoseconde. | |`typedef duration<long long, micro> microseconds;`| Synonyme pour un `duration` type qui a un cycle de 1 microseconde. | |`typedef duration<long long, milli> milliseconds;`| Synonyme pour un `duration` type qui a un cycle de 1 milliseconde. | |`typedef duration<long long> seconds;`| Synonyme pour un `duration` type qui a un cycle de 1 seconde. | |`typedef duration<int, ratio<60> > minutes;`| Synonyme pour un `duration` type qui a un cycle de 1 minute. | |`typedef duration<int, ratio<3600> > hours;`| Synonyme pour un `duration` type qui a un cycle de 1 heure. |

### <a name="literals"></a>Littéraux

**(C ++ 11)**  Le \<chrono > en-tête définit ce qui suit [littéraux définis par l’utilisateur](../cpp/user-defined-literals-cpp.md) que vous pouvez utiliser pour le plus grand confort, sécurité de type et la maintenance de votre code. Ces littéraux sont définis dans l'espace de noms inline `literals::chrono_literals` et sont dans la portée quand std::chrono est dans la portée.

|||
|-|-|
|opérateur d’heures » « h (unsigned long longue Val)|Spécifie les heures comme valeur intégrale.|
|durée\<double, ratio\<3600 >> opérateur « » h (long double Val)|Spécifie les heures comme valeur à virgule flottante.|
|minutes (opérateur « » min) (unsigned long long Val)|Spécifie les minutes comme valeur intégrale.|
|durée\<double, ratio\<60 >> (opérateur « » min) (long double Val)|Spécifie les minutes comme valeur à virgule flottante.|
|opérateur de secondes » « s (unsigned long longue Val)|Spécifie les minutes comme valeur intégrale.|
|durée\<double > opérateur « » s (long double Val)|Spécifie les secondes comme valeur à virgule flottante.|
|opérateur de millisecondes » « ms (unsigned long longue Val)|Spécifie les millisecondes comme valeur intégrale.|
|durée\<double, milli > opérateur « » ms (long double Val)|Spécifie les millisecondes comme valeur à virgule flottante.|
|opérateur de microsecondes « » us (unsigned long longue Val)|Spécifie les microsecondes comme valeur intégrale.|
|durée\<double, micro > opérateur « » us (long double Val)|Spécifie les microsecondes comme valeur à virgule flottante.|
|opérateur de nanosecondes » « ns (unsigned long longue Val)|Spécifie les nanosecondes comme valeur intégrale.|
|durée\<double, nano > opérateur « » ns (long double Val)|Spécifie les nanosecondes comme valeur à virgule flottante.|

Les exemples suivants montrent comment utiliser les littéraux chrono.

```cpp
constexpr auto day = 24h;
constexpr auto week = 24h* 7;
constexpr auto my_duration_unit = 108ms;
```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
