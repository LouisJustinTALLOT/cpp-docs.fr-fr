---
title: map, classe | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- map/std::map
- map/std::map::allocator_type
- map/std::map::const_iterator
- map/std::map::const_pointer
- map/std::map::const_reference
- map/std::map::const_reverse_iterator
- map/std::map::difference_type
- map/std::map::iterator
- map/std::map::key_compare
- map/std::map::key_type
- map/std::map::mapped_type
- map/std::map::pointer
- map/std::map::reference
- map/std::map::reverse_iterator
- map/std::map::size_type
- map/std::map::value_type
- map/std::map::at
- map/std::map::begin
- map/std::map::cbegin
- map/std::map::cend
- map/std::map::clear
- map/std::map::count
- map/std::map::crbegin
- map/std::map::crend
- map/std::map::emplace
- map/std::map::emplace_hint
- map/std::map::empty
- map/std::map::end
- map/std::map::equal_range
- map/std::map::erase
- map/std::map::find
- map/std::map::get_allocator
- map/std::map::insert
- map/std::map::key_comp
- map/std::map::lower_bound
- map/std::map::max_size
- map/std::map::rbegin
- map/std::map::rend
- map/std::map::size
- map/std::map::swap
- map/std::map::upper_bound
- map/std::map::value_comp
dev_langs: C++
helpviewer_keywords:
- std::map [C++]
- std::map [C++], allocator_type
- std::map [C++], const_iterator
- std::map [C++], const_pointer
- std::map [C++], const_reference
- std::map [C++], const_reverse_iterator
- std::map [C++], difference_type
- std::map [C++], iterator
- std::map [C++], key_compare
- std::map [C++], key_type
- std::map [C++], mapped_type
- std::map [C++], pointer
- std::map [C++], reference
- std::map [C++], reverse_iterator
- std::map [C++], size_type
- std::map [C++], value_type
- std::map [C++], at
- std::map [C++], begin
- std::map [C++], cbegin
- std::map [C++], cend
- std::map [C++], clear
- std::map [C++], count
- std::map [C++], crbegin
- std::map [C++], crend
- std::map [C++], emplace
- std::map [C++], emplace_hint
- std::map [C++], empty
- std::map [C++], end
- std::map [C++], equal_range
- std::map [C++], erase
- std::map [C++], find
- std::map [C++], get_allocator
- std::map [C++], insert
- std::map [C++], key_comp
- std::map [C++], lower_bound
- std::map [C++], max_size
- std::map [C++], rbegin
- std::map [C++], rend
- std::map [C++], size
- std::map [C++], swap
- std::map [C++], upper_bound
- std::map [C++], value_comp
ms.assetid: 7876f4c9-ebb4-4878-af1e-09364c43af0a
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d83bebb0953ee3ed7acec9e0e732cef6e5b3816f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="map-class"></a>map, classe
Utilisé pour le stockage et la récupération de données d’une collection dans laquelle chaque élément est une paire qui a à la fois une valeur de données et une clé de tri. La valeur de la clé est unique et est utilisée pour trier automatiquement les données.  
  
 La valeur d'un élément dans une classe map peut être modifiée directement. La valeur de clé est une constante non modifiable. Les valeurs de clés associées aux anciens éléments doivent être supprimées, et de nouvelles valeurs de clés doivent être insérées pour les nouveaux éléments.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Key,   
    class Type,   
    class Traits = less<Key>,   
    class Allocator=allocator<pair <const Key, Type>>>  
class map;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `Key`  
 Type de données clé à stocker dans la classe map.  
  
 `Type`  
 Type de données d'élément à stocker dans la classe map.  
  
 `Traits`  
 Type qui fournit un objet de fonction pouvant comparer deux valeurs d'éléments comme clés de tri afin de déterminer leur ordre relatif dans la classe map. Cet argument est facultatif et le prédicat binaire `less<Key>` est la valeur par défaut.  
  
 Dans C++14, vous pouvez activer la recherche hétérogène en spécifiant le prédicat std::less<> qui n’a aucun paramètre de type. Pour plus d’informations, consultez [Recherche hétérogène dans les conteneurs associatifs](../standard-library/stl-containers.md#sequence_containers).  
  
 `Allocator`  
 Type qui représente l'objet allocateur stocké qui contient des informations sur l'allocation et la désallocation de mémoire de la classe map. Cet argument est facultatif et sa valeur par défaut est `allocator<pair<const Key, Type> >`.  
  
## <a name="remarks"></a>Notes  
 La classe map de la bibliothèque standard C++ est :  
  
-   Un conteneur de taille variable qui récupère efficacement des valeurs d'éléments selon les valeurs de clés associées.  
  
-   Réversible, car elle fournit des itérateurs bidirectionnels pour accéder à ses éléments.  
  
-   Trié, car ses éléments sont classés par valeurs de clés selon une fonction de comparaison spécifiée.  
  
-   Unique, car chacun de ses éléments doit avoir une clé unique.  
  
-   Un conteneur associatif de paires, car ses valeurs de données d'éléments sont séparées de ses valeurs de clés.  
  
-   Une classe de modèle, car la fonctionnalité qu'elle fournit est générique et indépendante du type d'élément et du type de clé. Les types de données utilisés pour des éléments et des clés sont spécifiés comme paramètres dans le modèle de classe avec la fonction de comparaison et l'allocateur.  
  
 L’itérateur fourni par la classe map est bidirectionnel, mais les fonctions membres de classe [insert](#insert) et [map](#map) ont des versions qui prennent comme paramètres de modèle un itérateur d’entrée plus faible, dont les exigences des fonctionnalités sont moindres par rapport à celles garanties par la classe des itérateurs bidirectionnels. Les différents concepts d'itérateurs sont liés par des améliorations de leurs fonctionnalités. Chaque concept d'itérateur possède son propre ensemble de spécifications, et les algorithmes qui fonctionnent avec lui doivent être limités par ces spécifications. Un itérateur d'entrée peut être déréférencé pour faire référence à un objet et peut être incrémenté à l'itérateur suivant de la séquence.  
  
 Nous vous recommandons de baser le choix du type de conteneur sur le type de recherche et d'insertion qui est requis par l'application. Les conteneurs associatifs sont optimisés pour les opérations de recherche, d'insertion et de suppression. Les fonctions membres qui prennent en charge explicitement ces opérations les exécutent en un temps qui est, au pire des cas, proportionnel au logarithme du nombre d'éléments dans le conteneur. L'insertion d'éléments ne rend aucun itérateur non valide. La suppression d'éléments rend uniquement non valides les itérateurs qui pointaient spécifiquement vers les éléments supprimés.  
  
 Nous vous recommandons de faire de la classe map le conteneur associatif de premier choix lorsque des conditions qui associent des valeurs avec des clés sont remplies par l'application. Un modèle pour ce type de structure est une liste triée de mots clés à occurrence unique avec des valeurs de chaîne associées qui fournissent des définitions. Si un mot a plusieurs définitions correctes afin que la clé ne soit pas unique, il convient d'utiliser une classe multimap comme conteneur. Si seule la liste de mots est stockée, il convient d'utiliser un ensemble comme conteneur. Si plusieurs occurrences de mots sont autorisées, il convient d'utiliser une classe multiset.  
  
 La classe map trie les éléments qu’elle contrôle en appelant un objet de fonction stocké de type [key_compare](#key_compare). Cet objet stocké est une fonction de comparaison accessible en appelant la méthode [key_comp](#key_comp). En général, deux éléments donnés sont comparés pour déterminer si l'un est inférieur à l'autre ou s'ils sont équivalents. Comme tous les éléments sont comparés, une séquence classée d'éléments non équivalents est créée.  
  
> [!NOTE]
>  La fonction de comparaison est un prédicat binaire qui induit un ordre faible strict dans le sens mathématique du terme. Un prédicat binaire                     f(x,y) est un objet de fonction qui a deux objets d’arguments                     x et                     y, et la valeur de retour `true` ou `false`. Un tri appliqué à un ensemble est un ordre faible strict si le prédicat binaire est irréflexif, antisymétrique et transitif, et si l’équivalence est transitive (où deux objets                     x et                     y sont définis comme équivalents quand                     f(x,y) et                     f(y,x) ont la valeur `false`). Si la plus élevée des conditions d'égalité entre les clés remplace celle de l'équivalence, alors le tri devient total (dans le sens où tous les éléments sont classés les uns par rapport aux autres), et les clés correspondantes seront alors impossibles à différencier les unes des autres.  
>   
>  Dans C++14, vous pouvez activer la recherche hétérogène en spécifiant le prédicat `std::less<>` ou `std::greater<>` qui n'a aucun paramètre de type. Pour plus d’informations, consultez [Recherche hétérogène dans les conteneurs associatifs](../standard-library/stl-containers.md#sequence_containers).  
  
## <a name="members"></a>Membres  
  
### <a name="constructors"></a>Constructeurs  
  
|||  
|-|-|  
|[map](#map)|Construit une liste de taille spécifique ou contenant des éléments de valeurs spécifiques, ou contenant un `allocator` spécifique ou comme copie d'une autre classe map.|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[allocator_type](#allocator_type)|Typedef pour la classe `allocator` de l'objet map.|  
|[const_iterator](#const_iterator)|Typedef pour un itérateur bidirectionnel qui peut lire un élément `const` dans la classe map.|  
|[const_pointer](#const_pointer)|Typedef pour un pointeur vers un élément `const` d'une classe map.|  
|[const_reference](#const_reference)|Typedef pour une référence à un élément `const` stocké dans une classe map pour lire et effectuer des opérations `const`.|  
|[const_reverse_iterator](#const_reverse_iterator)|Type qui fournit un itérateur bidirectionnel capable de lire n'importe quel élément `const` dans la classe map.|  
|[difference_type](#difference_type)|Typedef entier signé pour le nombre d'éléments d'une classe map comprise dans une plage d'éléments pointés par des itérateurs.|  
|[iterator](#iterator)|Typedef pour un itérateur bidirectionnel qui permet de lire ou de modifier tout élément d'une classe map.|  
|[key_compare](#key_compare)|Typedef pour un objet de fonction qui peut comparer deux clés de tri pour déterminer l'ordre relatif de deux éléments d'une classe map.|  
|[key_type](#key_type)|Typedef pour la clé de tri stockée dans chaque élément de la classe map.|  
|[mapped_type](#mapped_type)|Typedef pour les données stockées dans chaque élément d'une classe map.|  
|[pointer](#pointer)|Typedef pour un pointeur vers un élément `const` d'une classe map.|  
|[reference](#reference)|Typedef pour une référence à un élément stocké dans une classe map.|  
|[reverse_iterator](#reverse_iterator)|Typedef pour un itérateur bidirectionnel qui permet de lire ou de modifier un élément d'une classe map inversée.|  
|[size_type](#size_type)|Typedef entier non signé pour le nombre d'éléments d'une classe map.|  
|[value_type](#value_type)|Typedef pour le type d'objet stocké comme élément dans une classe map.|  
  
### <a name="member-functions"></a>Fonctions membres  
  
|||  
|-|-|  
|[at](#at)|Recherche un élément avec une valeur de clé spécifiée.|  
|[begin](#begin)|Retourne un itérateur qui pointe vers le premier élément d'une classe map.|  
|[cbegin](#cbegin)|Retourne un itérateur const qui pointe vers le premier élément de la classe map.|  
|[cend](#cend)|Retourne un itérateur const de type past-the-end.|  
|[clear](#clear)|Efface tous les éléments d'une classe map.|  
|[count](#count)|Retourne le nombre d'éléments dans une classe map dont la clé correspond à celle spécifiée dans un paramètre.|  
|[crbegin](#crbegin)|Retourne un itérateur const qui pointe vers le premier élément d'une classe map inversée.|  
|[crend](#crend)|Retourne un itérateur const qui pointe vers l'emplacement après le dernier élément dans une classe map inversée.|  
|[emplace](#emplace)|Insère un élément construit sur place dans la classe map.|  
|[emplace_hint](#emplace_hint)|Insère un élément construit sur place dans la classe map, avec un indicateur de positionnement.|  
|[empty](#empty)|Retourne `true` si la classe map est vide.|  
|[end](#end)|Retourne l'itérateur past-the-end.|  
|[equal_range](#equal_range)|Retourne une paire d'itérateurs. Le premier itérateur de la paire pointe vers le premier élément d'un `map` avec une clé qui est supérieure à celle spécifiée. Le deuxième itérateur de la paire pointe vers le premier élément du `map` avec une clé dont la valeur est supérieure ou égale à la clé spécifiée.|  
|[erase](#erase)|Supprime un élément ou une plage d'éléments dans une classe map depuis les emplacement spécifiés.|  
|[find](#find)|Retourne un itérateur qui indique l'emplacement d'un élément dans une classe map qui a une clé égale à celle spécifiée.|  
|[get_allocator](#get_allocator)|Retourne une copie de l'objet `allocator` qui est utilisé pour construire la classe map.|  
|[insert](#insert)|Insère un élément ou une plage d'éléments dans la classe map à un emplacement spécifié.|  
|[key_comp](#key_comp)|Retourne une copie de l'objet de comparaison utilisé pour trier les clés dans une classe map.|  
|[lower_bound](#lower_bound)|Retourne un itérateur au premier élément d'une classe map qui a une valeur de clé supérieure ou égale à celle d'une clé spécifiée.|  
|[max_size](#max_size)|Retourne la longueur maximale de la classe map.|  
|[rbegin](#rbegin)|Retourne un itérateur qui pointe vers le premier élément d'une classe map inversée.|  
|[rend](#rend)|Retourne un itérateur qui pointe vers l'emplacement après le dernier élément dans une classe map inversée.|  
|[size](#size)|Retourne le nombre d'éléments d'une classe map.|  
|[swap](#swap)|Échange les éléments de deux classes map.|  
|[upper_bound](#upper_bound)|Retourne un itérateur au premier élément d'une classe map qui a une valeur de clé qui est supérieure ou égale à celle d'une clé spécifiée.|  
|[value_comp](#value_comp)|Récupère une copie de l'objet de comparaison utilisé pour trier les valeurs d'éléments dans une classe map.|  
  
### <a name="operators"></a>Opérateurs  
  
|||  
|-|-|  
|[operator&#91;&#93;](#op_at)|Insère un élément dans une classe map avec une valeur de clé spécifiée.|  
|[operator=](#op_eq)|Remplace les éléments d'une classe map par une copie d'une autre classe map.|  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** \<map>  
  
 **Espace de noms :** std  
  
##  <a name="allocator_type"></a>  map::allocator_type  
 Type qui représente la classe allocator pour l’objet map.  
  
```  
typedef Allocator allocator_type;  
```  
  
### <a name="example"></a>Exemple  
  Pour obtenir un exemple qui utilise `allocator_type`, consultez l’exemple de [get_allocator](#get_allocator).  
  
##  <a name="at"></a>  map::at  
 Recherche un élément avec une valeur de clé spécifiée.  
  
```  
Type& at(const Key& key);

const Type& at(const Key& key) const;
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|`key`|Valeur de clé à rechercher.|  
  
### <a name="return-value"></a>Valeur de retour  
 Référence à la valeur de données de l'élément trouvé.  
  
### <a name="remarks"></a>Notes  
 Si la valeur de clé de l’argument est introuvable, la fonction lève un objet de classe [out_of_range](../standard-library/out-of-range-class.md).  
  
### <a name="example"></a>Exemple  
  
```cpp  
// map_at.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
typedef std::map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// find and show elements  
    std::cout << "c1.at('a') == " << c1.at('a') << std::endl;   
    std::cout << "c1.at('b') == " << c1.at('b') << std::endl;   
    std::cout << "c1.at('c') == " << c1.at('c') << std::endl;   
  
    return (0);   
    }   
```  
  
##  <a name="begin"></a>  map::begin  
 Retourne un itérateur traitant le premier élément de la classe map.  
  
```  
const_iterator begin() const;

iterator begin();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Itérateur bidirectionnel traitant le premier élément de la classe map ou l’emplacement qui suit une classe map vide.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// map_begin.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map <int, int> m1;  
  
   map <int, int> :: iterator m1_Iter;  
   map <int, int> :: const_iterator m1_cIter;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 0, 0 ) );  
   m1.insert ( Int_Pair ( 1, 1 ) );  
   m1.insert ( Int_Pair ( 2, 4 ) );  
  
   m1_cIter = m1.begin ( );  
   cout << "The first element of m1 is " << m1_cIter -> first << endl;  
  
   m1_Iter = m1.begin ( );  
   m1.erase ( m1_Iter );  
  
   // The following 2 lines would err because the iterator is const  
   // m1_cIter = m1.begin ( );  
   // m1.erase ( m1_cIter );  
  
   m1_cIter = m1.begin( );  
   cout << "The first element of m1 is now " << m1_cIter -> first << endl;  
}  
```  
  
```Output  
The first element of m1 is 0  
The first element of m1 is now 1  
```  
  
##  <a name="cbegin"></a>  map::cbegin  
 Retourne un itérateur `const` qui traite l'emplacement situé immédiatement après le dernier élément d'une plage.  
  
```  
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Itérateur bidirectionnel `const` se rapportant au premier élément de la plage, ou emplacement situé juste après la fin d'une plage vide (pour une plage vide : `cbegin() == cend()`).  
  
### <a name="remarks"></a>Notes  
 Avec la valeur de retour `cbegin`, les éléments de la plage ne peuvent pas être modifiés.  
  
 Vous pouvez utiliser cette fonction membre à la place de la fonction membre `begin()` afin de garantir que la valeur de retour est `const_iterator`. En général, elle est utilisée conjointement avec le mot clé de déduction de type [auto](../cpp/auto-cpp.md), comme le montre l’exemple suivant. Dans cet exemple, `Container` est supposé être un conteneur modifiable (autre que `const`) de type indéfini prenant en charge `begin()` et `cbegin()`.  
  
```cpp  
auto i1 = Container.begin();
// i1 is Container<T>::iterator   
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator  
```  
  
##  <a name="cend"></a>  map::cend  
 Retourne un itérateur `const` qui traite l'emplacement situé immédiatement après le dernier élément d'une plage.  
  
```  
const_iterator cend() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Itérateur forward bidirectionnel `const` qui pointe juste après la fin de la plage.  
  
### <a name="remarks"></a>Notes  
 `cend` est utilisé pour vérifier si un itérateur a dépassé la fin de la plage.  
  
 Vous pouvez utiliser cette fonction membre à la place de la fonction membre `end()` afin de garantir que la valeur de retour est `const_iterator`. En général, elle est utilisée conjointement avec le mot clé de déduction de type [auto](../cpp/auto-cpp.md), comme le montre l’exemple suivant. Dans cet exemple, `Container` est supposé être un conteneur modifiable (autre que `const`) de type indéfini prenant en charge `end()` et `cend()`.  
  
```cpp  
auto i1 = Container.end();
// i1 is Container<T>::iterator   
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator  
```  
  
 La valeur retournée par `cend` ne doit pas être déréférencée.  
  
##  <a name="clear"></a>  map::clear  
 Efface tous les éléments d'une classe map.  
  
```  
void clear();
```  
  
### <a name="example"></a>Exemple  
  L'exemple suivant illustre l'utilisation de la fonction membre map::clear.  
  
```  
// map_clear.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    map<int, int> m1;  
    map<int, int>::size_type i;  
    typedef pair<int, int> Int_Pair;  
  
    m1.insert(Int_Pair(1, 1));  
    m1.insert(Int_Pair(2, 4));  
  
    i = m1.size();  
    cout << "The size of the map is initially "  
         << i << "." << endl;  
  
    m1.clear();  
    i = m1.size();  
    cout << "The size of the map after clearing is "  
         << i << "." << endl;  
}  
```  
  
```Output  
The size of the map is initially 2.  
The size of the map after clearing is 0.  
```  
  
##  <a name="const_iterator"></a>  map::const_iterator  
 Type qui fournit un itérateur bidirectionnel capable de lire un élément **const** dans la classe map.  
  
```  
typedef implementation-defined const_iterator;  
```  
  
### <a name="remarks"></a>Notes  
 Un type `const_iterator` ne peut pas être utilisé pour changer la valeur d'un élément.  
  
 Le `const_iterator` défini par la classe map pointe vers des éléments qui sont des objets de [value_type](#value_type), qui est de type `pair`\< **constKey**, **Type**>, dont le premier membre est la clé de l’élément et dont le deuxième membre est la référence mappée détenue par l’élément.  
  
 Pour déréférencer un `const_iterator` `cIter` pointe sur un élément dans un mappage, utilisez le  **->**  opérateur.  
  
 Pour accéder à la valeur de la clé de l’élément, utilisez `cIter` -> **first**, ce qui équivaut à (\* `cIter`). **first**.  
  
 Pour accéder à la valeur de la référence mappée de l’élément, utilisez `cIter` -> **second**, ce qui équivaut à (\* `cIter`). **second**.  
  
### <a name="example"></a>Exemple  
  Pour obtenir un exemple qui utilise `const_iterator`, consultez l’exemple de [begin](#begin).  
  
##  <a name="const_pointer"></a>  map::const_pointer  
 Type qui fournit un pointeur vers un élément **const** dans une classe map.  
  
```  
typedef typename allocator_type::const_pointer const_pointer;  
```  
  
### <a name="remarks"></a>Notes  
 Un type `const_pointer` ne peut pas être utilisé pour changer la valeur d'un élément.  
  
 Dans la plupart des cas, vous devez utiliser un [iterator](#iterator) pour accéder aux éléments dans un objet map.  
  
##  <a name="const_reference"></a>  map::const_reference  
 Type qui fournit une référence à un élément **const** stocké dans une classe map pour la lecture et l’exécution d’opérations **const**.  
  
```  
typedef typename allocator_type::const_reference const_reference;  
```  
  
### <a name="example"></a>Exemple  
  
```cpp  
// map_const_ref.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map <int, int> m1;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 1, 10 ) );  
   m1.insert ( Int_Pair ( 2, 20 ) );  
  
   // Declare and initialize a const_reference &Ref1   
   // to the key of the first element  
   const int &Ref1 = ( m1.begin( ) -> first );  
  
   // The following line would cause an error as the   
   // non-const_reference cannot be used to access the key  
   // int &Ref1 = ( m1.begin( ) -> first );  
  
   cout << "The key of first element in the map is "  
        << Ref1 << "." << endl;  
  
   // Declare and initialize a reference &Ref2   
   // to the data value of the first element  
   int &Ref2 = ( m1.begin( ) -> second );  
  
   cout << "The data value of first element in the map is "  
        << Ref2 << "." << endl;  
}  
```  
  
```Output  
The key of first element in the map is 1.  
The data value of first element in the map is 10.  
```  
  
##  <a name="const_reverse_iterator"></a>  map::const_reverse_iterator  
 Type qui fournit un itérateur bidirectionnel capable de lire un élément **const** dans la classe map.  
  
```  
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;  
```  
  
### <a name="remarks"></a>Notes  
 Un type `const_reverse_iterator` ne peut pas changer la valeur d’un élément. Il sert à itérer la classe map dans l’ordre inverse.  
  
 Le `const_reverse_iterator` défini par les points de la carte à des éléments qui sont des objets de [value_type](#value_type), qui est de type `pair<const Key, Type>`, dont le premier membre est la clé à l’élément et dont deuxième membre est la référence mappée détenue par l’élément.  
  
 Pour déréférencer un `const_reverse_iterator crIter` pointant vers un élément dans une classe map, utilisez l’opérateur **->**.  
  
 Pour accéder à la valeur de la clé pour l’élément, utilisez `crIter`  ->  **première**, ce qui équivaut à (\* `crIter`). **première**.  
  
 Pour accéder à la valeur de la référence mappée pour l’élément, utilisez `crIter`  ->  **deuxième**, ce qui équivaut à (\* `crIter`). **première**.  
  
### <a name="example"></a>Exemple  
  Pour savoir comment déclarer et utiliser `const_reverse_iterator`, consultez l’exemple [rend](#rend).  
  
##  <a name="count"></a>  map::count  
 Retourne le nombre d'éléments d'une classe map dont la clé correspond à une clé spécifiée par un paramètre.  
  
```  
size_type count(const Key& key) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `key`  
 Valeur de clé des éléments à mettre en correspondance à partir de la classe map.  
  
### <a name="return-value"></a>Valeur de retour  
 1 si la classe map contient un élément dont la clé de tri correspond à la clé du paramètre ; 0 si la classe map ne contient pas d'élément avec une clé correspondante.  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne le nombre d’éléments *x* dans la plage  
  
 [ `lower_bound` (_ *Key* ), `upper_bound` (\_ *Key* ) )  
  
 qui est 0 ou 1 dans le cas de map, qui est un conteneur associatif unique.  
  
### <a name="example"></a>Exemple  
  L'exemple suivant illustre l'utilisation de la fonction membre map::count.  
  
```  
// map_count.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    map<int, int> m1;  
    map<int, int>::size_type i;  
    typedef pair<int, int> Int_Pair;  
  
    m1.insert(Int_Pair(1, 1));  
    m1.insert(Int_Pair(2, 1));  
    m1.insert(Int_Pair(1, 4));  
    m1.insert(Int_Pair(2, 1));  
  
    // Keys must be unique in map, so duplicates are ignored  
    i = m1.count(1);  
    cout << "The number of elements in m1 with a sort key of 1 is: "  
         << i << "." << endl;  
  
    i = m1.count(2);  
    cout << "The number of elements in m1 with a sort key of 2 is: "  
         << i << "." << endl;  
  
    i = m1.count(3);  
    cout << "The number of elements in m1 with a sort key of 3 is: "  
         << i << "." << endl;  
}  
```  
  
```Output  
The number of elements in m1 with a sort key of 1 is: 1.  
The number of elements in m1 with a sort key of 2 is: 1.  
The number of elements in m1 with a sort key of 3 is: 0.  
```  
  
##  <a name="crbegin"></a>  map::crbegin  
 Retourne un itérateur const qui traite le premier élément d’une classe map inversée.  
  
```  
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Itérateur bidirectionnel inversé const qui traite le premier élément d’une classe [map](../standard-library/map-class.md) inversée, ou qui traite ce qui était le dernier élément de la classe `map` non inversée.  
  
### <a name="remarks"></a>Notes  
 `crbegin` est utilisé avec une classe `map` inversée de la même manière que [begin](#begin) est utilisé avec une classe `map`.  
  
 Avec la valeur de retour `crbegin`, l’objet `map` ne peut pas être changé.  
  
 Vous pouvez utiliser `crbegin` pour itérer un objet `map` vers l’arrière.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// map_crbegin.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   map <int, int> m1;  
  
   map <int, int> :: const_reverse_iterator m1_crIter;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 1, 10 ) );  
   m1.insert ( Int_Pair ( 2, 20 ) );  
   m1.insert ( Int_Pair ( 3, 30 ) );  
  
   m1_crIter = m1.crbegin( );  
   cout << "The first element of the reversed map m1 is "  
        << m1_crIter -> first << "." << endl;  
}  
```  
  
```Output  
The first element of the reversed map m1 is 3.  
```  
  
##  <a name="crend"></a>  map::crend  
 Retourne un itérateur const qui traite l’emplacement qui suit le dernier élément d’une classe map inversée.  
  
```  
const_reverse_iterator crend() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Itérateur bidirectionnel inversé const qui traite l’emplacement qui suit le dernier élément d’une classe [map](../standard-library/map-class.md) inversée (emplacement qui précédait le premier élément de la classe `map` non inversée).  
  
### <a name="remarks"></a>Notes  
 `crend` est utilisé avec une classe map inversée de la même manière que [end](#end) est utilisé avec une classe `map`.  
  
 Avec la valeur de retour `crend`, l'objet `map` ne peut pas être changé.  
  
 `crend` peut être utilisé pour déterminer si un itérateur inversé a atteint la fin de son objet `map`.  
  
 La valeur retournée par `crend` ne doit pas être déréférencée.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// map_crend.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map <int, int> m1;  
  
   map <int, int> :: const_reverse_iterator m1_crIter;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 1, 10 ) );  
   m1.insert ( Int_Pair ( 2, 20 ) );  
   m1.insert ( Int_Pair ( 3, 30 ) );  
  
   m1_crIter = m1.crend( );  
   m1_crIter--;  
   cout << "The last element of the reversed map m1 is "  
        << m1_crIter -> first << "." << endl;  
}  
```  
  
```Output  
The last element of the reversed map m1 is 1.  
```  
  
##  <a name="difference_type"></a>  map::difference_type  
 Type entier signé qui peut être utilisé pour représenter le nombre d’éléments d’une classe map au sein d’une plage, parmi les éléments pointés par les itérateurs.  
  
```  
typedef allocator_type::difference_type difference_type;  
```  
  
### <a name="remarks"></a>Notes  
 `difference_type` est le type retourné durant la soustraction ou l'incrémentation via les itérateurs du conteneur. `difference_type` est généralement utilisé pour représenter le nombre d’éléments de la plage *[ first,  last)* entre les itérateurs `first` et `last`. Il inclut l’élément vers lequel pointe `first` et la plage d’éléments allant jusqu’à l’élément (mais sans l’inclure) vers lequel pointe `last`.  
  
 Notez que même si `difference_type` est disponible pour tous les itérateurs qui répondent aux exigences d’un itérateur d’entrée, ce qui inclut la classe des itérateurs bidirectionnels prise en charge par les conteneurs réversibles tels que set, la soustraction entre les itérateurs est prise en charge uniquement par les itérateurs à accès aléatoire fournis par un conteneur à accès aléatoire (vector, par exemple).  
  
### <a name="example"></a>Exemple  
  
```cpp  
// map_diff_type.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <map>  
#include <algorithm>  
  
int main( )  
{  
   using namespace std;  
   map <int, int> m1;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 2, 20 ) );  
   m1.insert ( Int_Pair ( 1, 10 ) );  
   m1.insert ( Int_Pair ( 3, 20 ) );  
   m1.insert ( Int_Pair ( 2, 30 ) );  
  
   map <int, int>::iterator m1_Iter, m1_bIter, m1_eIter;  
   m1_bIter = m1.begin( );  
   m1_eIter = m1.end( );  
  
   // Count the number of elements in a map  
   map <int, int>::difference_type  df_count = 1;  
   m1_Iter = m1.begin( );  
   while ( m1_Iter != m1_eIter)  
   {  
      df_count++;  
      m1_Iter++;  
   }  
  
   cout << "The number of elements in the map m1 is: "   
        << df_count << "." << endl;  
}  
```  
  
```Output  
The number of elements in the map m1 is: 4.  
```  
  
##  <a name="emplace"></a>  map::emplace  
 Insère un élément construit sur place (sans opération de copie ni de déplacement) dans une classe map.  
  
```  
template <class... Args>  
pair<iterator, bool>  
emplace(
    Args&&... args);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|`args`|Arguments transmis pour construire un élément à insérer dans la classe map, sauf si elle contient déjà un élément dont la valeur est ordonnée de façon équivalente.|  
  
### <a name="return-value"></a>Valeur de retour  
 [Paire](../standard-library/pair-structure.md) dont le composant `bool` a la valeur true si une insertion a été effectuée, et false si la classe map contenait déjà un élément de valeur équivalente dans l’ordonnancement. Le composant itérateur de la paire de valeurs de retour pointe sur l'élément nouvellement inséré si le composant `bool` a la valeur true ou sur l'élément existant si le composant `bool` a la valeur false.  
  
 Pour accéder au composant itérateur d’un `pair` `pr`, utilisez `pr.first`; pour déréférencer, utilisez `*pr.first`. Pour accéder au composant `bool`, utilisez `pr.second`. Pour obtenir un exemple, voir l'exemple de code plus loin dans cet article.  
  
### <a name="remarks"></a>Notes  
 Aucun itérateur ou référence n’est invalidé par cette fonction.  
  
 Durant le placement, si une exception est levée, l’état du conteneur n’est pas modifié.  
  
 Le [value_type](#value_type) d’un élément est une paire, si bien que la valeur d’un élément est une paire ordonnée dont le premier composant est égal à la valeur de clé et le deuxième à la valeur de données de l’élément.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// map_emplace.cpp  
// compile with: /EHsc  
#include <map>  
#include <string>  
#include <iostream>  
  
using namespace std;  
  
template <typename M> void print(const M& m) {  
    cout << m.size() << " elements: ";  
  
    for (const auto& p : m) {  
        cout << "(" << p.first << ", " << p.second << ") ";  
    }  
  
    cout << endl;  
}  
  
int main()  
{  
    map<int, string> m1;  
  
    auto ret = m1.emplace(10, "ten");  
  
    if (!ret.second){  
        auto pr = *ret.first;  
        cout << "Emplace failed, element with key 10 already exists."  
            << endl << "  The existing element is (" << pr.first << ", " << pr.second << ")"  
            << endl;  
        cout << "map not modified" << endl;  
    }  
    else{  
        cout << "map modified, now contains ";  
        print(m1);  
    }  
    cout << endl;  
  
    ret = m1.emplace(10, "one zero");  
  
    if (!ret.second){  
        auto pr = *ret.first;  
        cout << "Emplace failed, element with key 10 already exists."  
            << endl << "  The existing element is (" << pr.first << ", " << pr.second << ")"  
            << endl;  
    }  
    else{  
        cout << "map modified, now contains ";  
        print(m1);  
    }  
    cout << endl;  
}  
  
```  
  
##  <a name="emplace_hint"></a>  map::emplace_hint  
 Insère un élément construit sur place (sans opération de copie ni de déplacement) avec un indicateur de positionnement.  
  
```  
template <class... Args>  
iterator emplace_hint(
    const_iterator where,  
    Args&&... args);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|`args`|Arguments transmis pour construire un élément à insérer dans la classe map, sauf si celle-ci contient déjà cet élément ou, plus généralement, si elle contient déjà un élément dont la clé est ordonnée de façon équivalente.|  
|`where`|Emplacement où commencer à rechercher le point d'insertion correct. (Si ce point précède immédiatement `where`, l'insertion peut se produire dans le temps fixe amorti plutôt que dans le temps logarithmique.)|  
  
### <a name="return-value"></a>Valeur de retour  
 Itérateur vers l’élément qui vient d’être inséré.  
  
 Si l’insertion a échoué car l’élément existe déjà, retourne un itérateur vers l’élément existant avec sa clé.  
  
### <a name="remarks"></a>Notes  
 Aucun itérateur ou référence n’est invalidé par cette fonction.  
  
 Durant le placement, si une exception est levée, l’état du conteneur n’est pas modifié.  
  
 Le [value_type](#value_type) d’un élément est une paire, si bien que la valeur d’un élément est une paire ordonnée dont le premier composant est égal à la valeur de clé et le deuxième à la valeur de données de l’élément.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// map_emplace.cpp  
// compile with: /EHsc  
#include <map>  
#include <string>  
#include <iostream>  
  
using namespace std;  
  
template <typename M> void print(const M& m) {  
    cout << m.size() << " elements: " << endl;  
  
    for (const auto& p : m) {  
        cout << "(" << p.first <<  "," << p.second << ") ";  
    }  
  
    cout << endl;  
}  
  
int main()  
{  
    map<string, string> m1;  
  
    // Emplace some test data  
    m1.emplace("Anna", "Accounting");  
    m1.emplace("Bob", "Accounting");  
    m1.emplace("Carmine", "Engineering");  
  
    cout << "map starting data: ";  
    print(m1);  
    cout << endl;  
  
    // Emplace with hint  
    // m1.end() should be the "next" element after this emplacement  
    m1.emplace_hint(m1.end(), "Doug", "Engineering");  
  
    cout << "map modified, now contains ";  
    print(m1);  
    cout << endl;  
}  
  
```  
  
##  <a name="empty"></a>  map::empty  
 Teste si une classe map est vide.  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 **true** si la classe map est vide. **false** si la classe map n’est pas vide.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// map_empty.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map <int, int> m1, m2;  
  
   typedef pair <int, int> Int_Pair;  
   m1.insert ( Int_Pair ( 1, 1 ) );  
  
   if ( m1.empty( ) )  
      cout << "The map m1 is empty." << endl;  
   else  
      cout << "The map m1 is not empty." << endl;  
  
   if ( m2.empty( ) )  
      cout << "The map m2 is empty." << endl;  
   else  
      cout << "The map m2 is not empty." << endl;  
}  
```  
  
```Output  
The map m1 is not empty.  
The map m2 is empty.  
```  
  
##  <a name="end"></a>  map::end  
 Retourne l'itérateur past-the-end.  
  
```  
const_iterator end() const;

 
 
iterator end();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Itérateur de type past-the-end. Si la classe map est vide, `map::end() == map::begin()`.  
  
### <a name="remarks"></a>Notes  
 **end** est utilisé pour déterminer si un itérateur a dépassé la fin de sa classe map.  
  
 La valeur retournée par **end** ne doit pas être déréférencée.  
  
 Pour obtenir un exemple de code, consultez [map::find](#find).  
  
##  <a name="equal_range"></a>  map::equal_range  
 Retourne une paire d’itérateurs qui représentent la [lower_bound](#lower_bound) et la [upper_bound](#upper_bound) de la clé.  
  
```  
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```  
  
### <a name="parameters"></a>Paramètres  
 `key`  
 Valeur de clé d’argument à comparer à la clé de tri d’un élément de la classe map dans laquelle la recherche est effectuée.  
  
### <a name="return-value"></a>Valeur de retour  
 Pour accéder au premier itérateur d’une paire `pr` retournée par la fonction membre, utilisez `pr`. **first**, et pour déréférencer l’itérateur de la limite inférieure (lower_bound), utilisez \*( `pr`. **first**). Pour accéder au second itérateur d’une paire `pr` retournée par la fonction membre, utilisez `pr`. **second**, et pour déréférencer l’itérateur de la limite supérieure (upper_bound), utilisez \*( `pr`. **second**).  
  
### <a name="example"></a>Exemple  
  
```cpp  
// map_equal_range.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;   
   typedef map <int, int, less<int> > IntMap;  
   IntMap m1;  
   map <int, int> :: const_iterator m1_RcIter;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 1, 10 ) );  
   m1.insert ( Int_Pair ( 2, 20 ) );  
   m1.insert ( Int_Pair ( 3, 30 ) );  
  
   pair <IntMap::const_iterator, IntMap::const_iterator> p1, p2;  
   p1 = m1.equal_range( 2 );  
  
   cout << "The lower bound of the element with "  
        << "a key of 2 in the map m1 is: "  
        << p1.first -> second << "." << endl;  
  
   cout << "The upper bound of the element with "  
        << "a key of 2 in the map m1 is: "  
        << p1.second -> second << "." << endl;  
  
   // Compare the upper_bound called directly   
   m1_RcIter = m1.upper_bound( 2 );  
  
   cout << "A direct call of upper_bound( 2 ) gives "  
        << m1_RcIter -> second << "," << endl  
        << " matching the 2nd element of the pair"  
        << " returned by equal_range( 2 )." << endl;  
  
   p2 = m1.equal_range( 4 );  
  
   // If no match is found for the key,  
   // both elements of the pair return end( )  
   if ( ( p2.first == m1.end( ) ) && ( p2.second == m1.end( ) ) )  
      cout << "The map m1 doesn't have an element "  
           << "with a key less than 40." << endl;  
   else  
      cout << "The element of map m1 with a key >= 40 is: "  
           << p2.first -> first << "." << endl;  
}  
```  
  
```Output  
The lower bound of the element with a key of 2 in the map m1 is: 20.  
The upper bound of the element with a key of 2 in the map m1 is: 30.  
A direct call of upper_bound( 2 ) gives 30,  
 matching the 2nd element of the pair returned by equal_range( 2 ).  
The map m1 doesn't have an element with a key less than 40.  
```  
  
##  <a name="erase"></a>  map::erase  
 Supprime des positions spécifiées un élément ou une plage d’éléments compris dans une classe map, ou supprime les éléments qui correspondent à une clé spécifiée.  
  
```  
iterator erase(
    const_iterator Where);

 
iterator erase(
    const_iterator First,  
    const_iterator Last);

 
size_type erase(
    const key_type& Key);
```  
  
### <a name="parameters"></a>Paramètres  
 `Where`  
 Position de l’élément à supprimer.  
  
 `First`  
 Position du premier élément à supprimer.  
  
 `Last`  
 Position juste après le dernier élément à supprimer.  
  
 `Key`  
 Valeur de clé des éléments à supprimer.  
  
### <a name="return-value"></a>Valeur de retour  
 Pour les deux premières fonctions membres, itérateur bidirectionnel qui désigne le premier élément restant après que tous les éléments ont été supprimés ou élément à la fin de la classe map si aucun élément de ce type n’existe.  
  
 Pour la troisième fonction membre, retourne le nombre d’éléments qui ont été supprimés de la classe map.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// map_erase.cpp  
// compile with: /EHsc  
#include <map>  
#include <string>  
#include <iostream>  
#include <iterator> // next() and prev() helper functions  
#include <utility>  // make_pair()  
  
using namespace std;  
  
using mymap = map<int, string>;  
  
void printmap(const mymap& m) {  
    for (const auto& elem : m) {  
        cout << " [" << elem.first << ", " << elem.second << "]";  
    }  
    cout << endl << "size() == " << m.size() << endl << endl;  
}  
  
int main()  
{  
    mymap m1;  
  
    // Fill in some data to test with, one at a time  
    m1.insert(make_pair(1, "A"));  
    m1.insert(make_pair(2, "B"));  
    m1.insert(make_pair(3, "C"));  
    m1.insert(make_pair(4, "D"));  
    m1.insert(make_pair(5, "E"));  
  
    cout << "Starting data of map m1 is:" << endl;  
    printmap(m1);  
    // The 1st member function removes an element at a given position  
    m1.erase(next(m1.begin()));  
    cout << "After the 2nd element is deleted, the map m1 is:" << endl;  
    printmap(m1);  
  
    // Fill in some data to test with, one at a time, using an intializer list  
    mymap m2  
    {  
        { 10, "Bob" },  
        { 11, "Rob" },  
        { 12, "Robert" },  
        { 13, "Bert" },  
        { 14, "Bobby" }  
    };  
  
    cout << "Starting data of map m2 is:" << endl;  
    printmap(m2);  
    // The 2nd member function removes elements  
    // in the range [First, Last)  
    m2.erase(next(m2.begin()), prev(m2.end()));  
    cout << "After the middle elements are deleted, the map m2 is:" << endl;  
    printmap(m2);  
  
    mymap m3;  
  
    // Fill in some data to test with, one at a time, using emplace  
    m3.emplace(1, "red");  
    m3.emplace(2, "yellow");  
    m3.emplace(3, "blue");  
    m3.emplace(4, "green");  
    m3.emplace(5, "orange");  
    m3.emplace(6, "purple");  
    m3.emplace(7, "pink");  
  
    cout << "Starting data of map m3 is:" << endl;  
    printmap(m3);  
    // The 3rd member function removes elements with a given Key  
    mymap::size_type count = m3.erase(2);  
    // The 3rd member function also returns the number of elements removed  
    cout << "The number of elements removed from m3 is: " << count << "." << endl;  
    cout << "After the element with a key of 2 is deleted, the map m3 is:" << endl;  
    printmap(m3);  
}  
  
```  
  
##  <a name="find"></a>  map::find  
 Retourne un itérateur qui fait référence à l'emplacement d'un élément dans un mappage ayant une clé équivalente à la clé spécifiée.  
  
```  
iterator find(const Key& key);

 
const_iterator find(const Key& key) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `key`  
 Valeur de clé qui doit correspondre à la clé de tri d'un élément du mappage dans lequel la recherche est effectuée.  
  
### <a name="return-value"></a>Valeur de retour  
 Itérateur qui fait référence à l’emplacement d’un élément ayant la clé spécifiée ou emplacement qui suit le dernier élément de la classe map (`map::end()`), si aucune correspondance n’est trouvée pour la clé.  
  
### <a name="remarks"></a>Notes  
 La fonction membre retourne un itérateur qui fait référence à un élément du mappage dont la clé de tri est équivalente à l’argument key sous un prédicat binaire qui induit un classement basé sur une relation d’infériorité.  
  
 Si la valeur de retour de **find** est affectée à un **const_iterator**, l’objet map ne peut pas être changé. Si la valeur de retour de **find** est affectée à un **iterator**, l’objet map peut être changé.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// compile with: /EHsc /W4 /MTd  
#include <map>  
#include <iostream>  
#include <vector>  
#include <string>  
#include <utility>  // make_pair()  
  
using namespace std;  
  
template <typename A, typename B> void print_elem(const pair<A, B>& p) {  
    cout << "(" << p.first << ", " << p.second << ") ";  
}  
  
template <typename T> void print_collection(const T& t) {  
    cout << t.size() << " elements: ";  
  
    for (const auto& p : t) {  
        print_elem(p);  
    }  
    cout << endl;  
}  
  
template <typename C, class T> void findit(const C& c, T val) {  
    cout << "Trying find() on value " << val << endl;  
    auto result = c.find(val);  
    if (result != c.end()) {  
        cout << "Element found: "; print_elem(*result); cout << endl;  
    } else {  
        cout << "Element not found." << endl;  
    }  
}  
  
int main()  
{  
    map<int, string> m1({ { 40, "Zr" }, { 45, "Rh" } });  
    cout << "The starting map m1 is (key, value):" << endl;  
    print_collection(m1);  
  
    vector<pair<int, string>> v;  
    v.push_back(make_pair(43, "Tc"));  
    v.push_back(make_pair(41, "Nb"));  
    v.push_back(make_pair(46, "Pd"));  
    v.push_back(make_pair(42, "Mo"));  
    v.push_back(make_pair(44, "Ru"));  
    v.push_back(make_pair(44, "Ru")); // attempt a duplicate  
  
    cout << "Inserting the following vector data into m1:" << endl;  
    print_collection(v);  
  
    m1.insert(v.begin(), v.end());  
  
    cout << "The modified map m1 is (key, value):" << endl;  
    print_collection(m1);  
    cout << endl;  
    findit(m1, 45);  
    findit(m1, 6);  
}  
  
```  
  
##  <a name="get_allocator"></a>  map::get_allocator  
 Retourne une copie de l’objet allocateur utilisé pour construire la classe map.  
  
```  
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Allocateur utilisé par la classe map.  
  
### <a name="remarks"></a>Notes  
 Les allocateurs de la classe map spécifient la façon dont la classe gère le stockage. Les allocateurs par défaut fournis avec les classes de conteneur de la bibliothèque standard C++ sont suffisants pour la plupart des besoins en programmation. L'écriture et l'utilisation de votre propre classe d'allocateur font l'objet d'une rubrique avancée du langage C++.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// map_get_allocator.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map <int, int>::allocator_type m1_Alloc;  
   map <int, int>::allocator_type m2_Alloc;  
   map <int, double>::allocator_type m3_Alloc;  
   map <int, int>::allocator_type m4_Alloc;  
  
   // The following lines declare objects  
   // that use the default allocator.  
   map <int, int> m1;  
   map <int, int, allocator<int> > m2;  
   map <int, double, allocator<double> > m3;  
  
   m1_Alloc = m1.get_allocator( );  
   m2_Alloc = m2.get_allocator( );  
   m3_Alloc = m3.get_allocator( );  
  
   cout << "The number of integers that can be allocated\n"  
        << "before free memory is exhausted: "  
        << m2.max_size( ) << ".\n" << endl;  
  
   cout << "The number of doubles that can be allocated\n"  
        << "before free memory is exhausted: "  
        << m3.max_size( ) <<  ".\n" << endl;  
  
   // The following line creates a map m4  
   // with the allocator of map m1.  
   map <int, int> m4( less<int>( ), m1_Alloc );  
  
   m4_Alloc = m4.get_allocator( );  
  
   // Two allocators are interchangeable if  
   // storage allocated from each can be  
   // deallocated with the other  
   if( m1_Alloc == m4_Alloc )     
   {  
      cout << "The allocators are interchangeable." << endl;  
   }  
   else     
   {  
      cout << "The allocators are not interchangeable." << endl;  
   }  
}  
```  
  
##  <a name="insert"></a>  map::insert  
 Insère un élément ou une plage d'éléments dans une classe map.  
  
```  
// (1) single element  
pair<iterator, bool> insert(
    const value_type& Val);

 
// (2) single element, perfect forwarded  
template <class ValTy>  
pair<iterator, bool>  
insert(
    ValTy&& Val);

 
// (3) single element with hint  
iterator insert(
    const_iterator Where,  
    const value_type& Val);

 
// (4) single element, perfect forwarded, with hint  
template <class ValTy>  
iterator insert(
    const_iterator Where,  
    ValTy&& Val);

 
// (5) range   
template <class InputIterator>   
void insert(
    InputIterator First,  
    InputIterator Last);

 
// (6) initializer list  
void insert(
    initializer_list<value_type>  
IList);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|`Val`|Valeur d'un élément à insérer dans la classe map sauf si elle contient déjà un élément dont la clé est classée de manière équivalente.|  
|`Where`|Emplacement où commencer à rechercher le point d'insertion correct. (Si ce point précède immédiatement `Where`, l'insertion peut se produire dans le temps fixe amorti plutôt que dans le temps logarithmique.)|  
|`ValTy`|Paramètre de modèle qui spécifie le type d’argument que la classe map peut utiliser pour construire un élément de [value_type](#value_type), et effectue un transfert parfait de `Val` comme argument.|  
|`First`|Position du premier élément à copier.|  
|`Last`|Position juste au-delà du dernier élément à copier.|  
|`InputIterator`|Argument de fonction de modèle qui remplit les conditions requises par un [itérateur d’entrée](../standard-library/input-iterator-tag-struct.md) qui pointe vers des éléments d’un type pouvant servir à construire des objets [value_type](#value_type).|  
|`IList`|[initializer_list](../standard-library/initializer-list.md) à partir de laquelle copier les éléments.|  
  
### <a name="return-value"></a>Valeur de retour  
 Les fonctions membres à un seul élément, (1) et (2), retournent une [paire](../standard-library/pair-structure.md) dont le composant `bool` a la valeur true si une insertion a été effectuée, et false si la classe map contenait déjà un élément dont la clé avait une valeur équivalente dans le classement. Le composant itérateur de la paire de valeurs de retour pointe sur l'élément nouvellement inséré si le composant `bool` a la valeur true ou sur l'élément existant si le composant `bool` a la valeur false.  
  
 Les fonctions membres à un élément avec indicateur, (3) et (4), retournent un itérateur qui pointe sur la position où le nouvel élément a été inséré dans la classe map ou, si un élément avec une clé équivalente existe déjà, sur l'élément existant.  
  
### <a name="remarks"></a>Notes  
 Aucun itérateur, pointeur ou référence n'est invalidé par cette fonction.  
  
 Durant l'insertion d'un seul élément, si une exception est levée, l'état du conteneur n'est pas modifié. Durant l'insertion de plusieurs éléments, si une exception est levée, le conteneur reste dans un état non spécifié mais valide.  
  
 Pour accéder au composant itérateur d'une `pair` `pr` qui est retournée par les fonctions membres à un élément, utilisez `pr.first` ; pour déréférencer l'itérateur dans la paire retournée, utilisez `*pr.first`, qui vous donne un élément. Pour accéder au composant `bool`, utilisez `pr.second`. Pour obtenir un exemple, voir l'exemple de code plus loin dans cet article.  
  
 Le [value_type](#value_type) d’un conteneur est un typedef qui appartient au conteneur et, pour la classe map, `map<K, V>::value_type` est `pair<const K, V>`. La valeur d'un élément est une paire ordonnée dans laquelle le premier composant est égal à la valeur de clé et le second composant est égal à la valeur de données de l'élément.  
  
 La fonction membre de plage (5) insère la séquence de valeurs d'éléments dans une classe map qui correspond à chaque élément traité par un itérateur dans la plage `[First, Last)` ; ainsi, `Last` n'est pas inséré. La fonction membre de conteneur `end()` fait référence à la position qui suit le dernier élément du conteneur. Par exemple, l'instruction `m.insert(v.begin(), v.end());` tente d'insérer tous les éléments de `v` dans `m`. Seuls les éléments qui ont des valeurs uniques dans la plage sont insérés. Les doublons sont ignorés. Pour savoir quels éléments sont rejetés, utilisez les versions à un élément de `insert`.  
  
 La fonction membre de liste d’initialiseurs (6) utilise une [initializer_list](../standard-library/initializer-list.md) pour copier des éléments dans la classe map.  
  
 Pour plus d’informations sur l’insertion d’un élément construit sur place (sans opération de copie ni de déplacement), consultez [map::emplace](#emplace) et [map::emplace_hint](#emplace_hint).  
  
### <a name="example"></a>Exemple  
  
```cpp  
// map_insert.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
#include <string>  
#include <vector>  
#include <utility>  // make_pair()  
  
using namespace std;  
  
template <typename M> void print(const M& m) {  
    cout << m.size() << " elements: ";  
  
    for (const auto& p : m) {  
        cout << "(" << p.first << ", " << p.second << ") ";  
    }  
  
    cout << endl;  
}  
  
int main()  
{  
  
    // insert single values   
    map<int, int> m1;  
    // call insert(const value_type&) version  
    m1.insert({ 1, 10 });  
    // call insert(ValTy&&) version   
    m1.insert(make_pair(2, 20));  
  
    cout << "The original key and mapped values of m1 are:" << endl;  
    print(m1);  
  
    // intentionally attempt a duplicate, single element  
    auto ret = m1.insert(make_pair(1, 111));  
    if (!ret.second){  
        auto pr = *ret.first;  
        cout << "Insert failed, element with key value 1 already exists."  
            << endl << "  The existing element is (" << pr.first << ", " << pr.second << ")"  
            << endl;  
    }  
    else{  
        cout << "The modified key and mapped values of m1 are:" << endl;  
        print(m1);  
    }  
    cout << endl;  
  
    // single element, with hint  
    m1.insert(m1.end(), make_pair(3, 30));  
    cout << "The modified key and mapped values of m1 are:" << endl;  
    print(m1);  
    cout << endl;  
  
    // The templatized version inserting a jumbled range  
    map<int, int> m2;  
    vector<pair<int, int>> v;  
    v.push_back(make_pair(43, 294));  
    v.push_back(make_pair(41, 262));  
    v.push_back(make_pair(45, 330));  
    v.push_back(make_pair(42, 277));  
    v.push_back(make_pair(44, 311));  
  
    cout << "Inserting the following vector data into m2:" << endl;  
    print(v);  
  
    m2.insert(v.begin(), v.end());  
  
    cout << "The modified key and mapped values of m2 are:" << endl;  
    print(m2);  
    cout << endl;  
  
    // The templatized versions move-constructing elements  
    map<int, string>  m3;  
    pair<int, string> ip1(475, "blue"), ip2(510, "green");  
  
    // single element  
    m3.insert(move(ip1));  
    cout << "After the first move insertion, m3 contains:" << endl;  
    print(m3);  
  
    // single element with hint  
    m3.insert(m3.end(), move(ip2));  
    cout << "After the second move insertion, m3 contains:" << endl;  
    print(m3);  
    cout << endl;  
  
    map<int, int> m4;  
    // Insert the elements from an initializer_list  
    m4.insert({ { 4, 44 }, { 2, 22 }, { 3, 33 }, { 1, 11 }, { 5, 55 } });  
    cout << "After initializer_list insertion, m4 contains:" << endl;  
    print(m4);  
    cout << endl;  
}  
  
```  
  
##  <a name="iterator"></a>  map::iterator  
 Type qui fournit un itérateur bidirectionnel capable de lire ou de modifier tout élément d’une classe map.  
  
```  
typedef implementation-defined iterator;  
```  
  
### <a name="remarks"></a>Notes  
 L’**iterator** défini par la classe map pointe vers des éléments qui sont des objets de [value_type](#value_type), qui est de type `pair`*\<***constKey**, **Type***>*, dont le premier membre est la clé de l’élément et dont le deuxième membre est la référence mappée détenue par l’élément.  
  
 Pour déréférencer un **iterator**`Iter` pointant vers un élément dans une classe map, utilisez l’opérateur **->**.  
  
 Pour accéder à la valeur de la clé de l’élément, utilisez `Iter` -> **first**, ce qui équivaut à (\* `Iter`). **first**. Pour accéder à la valeur de la référence mappée de l’élément, utilisez `Iter` -> **second**, ce qui équivaut à (\* `Iter`). **second**.  
  
### <a name="example"></a>Exemple  
  Pour savoir comment déclarer et utiliser **iterator**, consultez l’exemple de [begin](#begin).  
  
##  <a name="key_comp"></a>  map::key_comp  
 Récupère une copie de l’objet de comparaison utilisé pour trier les clés au sein d’une classe map.  
  
```  
key_compare key_comp() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne l’objet de fonction utilisé par une classe map pour ordonner ses éléments.  
  
### <a name="remarks"></a>Notes  
 L’objet stocké définit la fonction membre  
  
 **bool operator**( **constKey&**`left`, **const Key&**`right`);  
  
 qui retourne **true** si `left` précède et n’est pas égal à `right` dans l’ordre de tri.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// map_key_comp.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   map <int, int, less<int> > m1;  
   map <int, int, less<int> >::key_compare kc1 = m1.key_comp( ) ;  
   bool result1 = kc1( 2, 3 ) ;  
   if( result1 == true )  
   {  
      cout << "kc1( 2,3 ) returns value of true, "  
           << "where kc1 is the function object of m1."  
           << endl;  
   }  
   else     
   {  
      cout << "kc1( 2,3 ) returns value of false "  
           << "where kc1 is the function object of m1."  
           << endl;  
   }  
  
   map <int, int, greater<int> > m2;  
   map <int, int, greater<int> >::key_compare kc2 = m2.key_comp( );  
   bool result2 = kc2( 2, 3 ) ;  
   if( result2 == true )  
   {  
      cout << "kc2( 2,3 ) returns value of true, "  
           << "where kc2 is the function object of m2."  
           << endl;  
   }  
   else     
   {  
      cout << "kc2( 2,3 ) returns value of false, "  
           << "where kc2 is the function object of m2."  
           << endl;  
   }  
}  
```  
  
```Output  
kc1( 2,3 ) returns value of true, where kc1 is the function object of m1.  
kc2( 2,3 ) returns value of false, where kc2 is the function object of m2.  
```  
  
##  <a name="key_compare"></a>  map::key_compare  
 Type qui fournit un objet de fonction pouvant comparer deux clés de tri pour déterminer l’ordre relatif de deux éléments dans la classe map.  
  
```  
typedef Traits key_compare;  
```  
  
### <a name="remarks"></a>Notes  
 `key_compare` est un synonyme du paramètre de modèle `Traits`.  
  
 Pour plus d’informations sur `Traits`, consultez la rubrique [map, classe](../standard-library/map-class.md).  
  
### <a name="example"></a>Exemple  
  Pour découvrir comment déclarer et utiliser `key_compare`, consultez l’exemple relatif à [key_comp](#key_comp).  
  
##  <a name="key_type"></a>  map::key_type  
 Type qui décrit la clé de tri stockée dans chaque élément de la classe map.  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>Notes  
 `key_type` est un synonyme du paramètre de modèle `Key`.  
  
 Pour plus d’informations sur `Key`, consultez la section Remarques de la rubrique [map, classe](../standard-library/map-class.md).  
  
### <a name="example"></a>Exemple  
  Pour découvrir comment déclarer et utiliser `key_type`, consultez l’exemple relatif à [value_type](#value_type).  
  
##  <a name="lower_bound"></a>  map::lower_bound  
 Retourne un itérateur pointant vers le premier élément d’une classe map qui a une valeur de clé supérieure ou égale à celle d’une clé spécifiée.  
  
```  
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `key`  
 Valeur de clé d’argument à comparer à la clé de tri d’un élément de la classe map dans laquelle la recherche est effectuée.  
  
### <a name="return-value"></a>Valeur de retour  
 **iterator** ou `const_iterator` qui traite l’emplacement d’un élément dans une classe map ayant une clé supérieure ou égale à la clé d’argument, ou qui traite l’emplacement suivant le dernier élément dans la classe map si aucune correspondance n’est trouvée pour la clé.  
  
 Si la valeur de retour de `lower_bound` est assignée à un `const_iterator`, l’objet map ne peut pas être changé. Si la valeur de retour de `lower_bound` est affectée à un **iterator**, l’objet map peut être changé.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// map_lower_bound.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   map <int, int> m1;  
   map <int, int> :: const_iterator m1_AcIter, m1_RcIter;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 1, 10 ) );  
   m1.insert ( Int_Pair ( 2, 20 ) );  
   m1.insert ( Int_Pair ( 3, 30 ) );  
  
   m1_RcIter = m1.lower_bound( 2 );  
   cout << "The first element of map m1 with a key of 2 is: "  
        << m1_RcIter -> second << "." << endl;  
  
   // If no match is found for this key, end( ) is returned  
   m1_RcIter = m1. lower_bound ( 4 );  
  
   if ( m1_RcIter == m1.end( ) )  
      cout << "The map m1 doesn't have an element "  
           << "with a key of 4." << endl;  
   else  
      cout << "The element of map m1 with a key of 4 is: "  
           << m1_RcIter -> second << "." << endl;  
  
   // The element at a specific location in the map can be found   
   // using a dereferenced iterator addressing the location  
   m1_AcIter = m1.end( );  
   m1_AcIter--;  
   m1_RcIter = m1. lower_bound ( m1_AcIter -> first );  
   cout << "The element of m1 with a key matching "  
        << "that of the last element is: "  
        << m1_RcIter -> second << "." << endl;  
}  
```  
  
```Output  
The first element of map m1 with a key of 2 is: 20.  
The map m1 doesn't have an element with a key of 4.  
The element of m1 with a key matching that of the last element is: 30.  
```  
  
##  <a name="map"></a>  map::map  
 Construit une classe map vide ou une copie de l’ensemble, ou d’une partie d’une autre classe map.  
  
```  
map();

explicit map(
    const Traits& Comp);

map(
    const Traits& Comp,  
    const Allocator& Al);

map(
    const map& Right);

map(
    map&& Right);

map(
    initializer_list<value_type> IList);

map(
    initializer_list<value_type> IList,  
    const Traits& Comp);

map(
    initializer_list<value_type> IList,  
    const Traits& Comp,   
    const Allocator& Allocator);

template <class InputIterator>  
map(
 InputIterator First,  
    InputIterator Last);

template <class InputIterator>  
map(
 InputIterator First,  
    InputIterator Last,  
    const Traits& Comp);

template <class InputIterator>  
map(
 InputIterator First,  
    InputIterator Last,  
    const Traits& Comp,  
    const Allocator& Al);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|`Al`|Classe d’allocateur de stockage à utiliser pour cet objet map, qui est par défaut `Allocator`.|  
|`Comp`|Fonction de comparaison de type `const Traits` utilisée pour ordonner les éléments dans la classe map (par défaut, `hash_compare`).|  
|`Right`|Mappage dont l’ensemble construit doit être une copie.|  
|`First`|Position du premier élément de la plage d'éléments à copier.|  
|`Last`|Position du premier élément au-delà de la plage d'éléments à copier.|  
|`IList`|Initializer_list à partir de laquelle les éléments doivent être copiés.|  
  
### <a name="remarks"></a>Notes  
 Tous les constructeurs stockent un type d’objet allocateur qui gère le stockage de mémoire de la classe map et peut être retourné ultérieurement en appelant [get_allocator](#get_allocator). Le paramètre d’allocateur est souvent omis dans les déclarations de classe et des macros de prétraitement sont utilisées pour substituer des allocateurs de remplacement.  
  
 Tous les constructeurs initialisent leur classe map.  
  
 Tous les constructeurs stockent un objet de fonction de type Traits, qui est utilisé pour classer les clés de la classe map et qui peut être retourné ultérieurement en appelant [key_comp](#key_comp).  
  
 Les trois premiers constructeurs spécifient une classe map initiale vide. Le deuxième constructeur spécifie le type de fonction de comparaison ( `Comp`) à utiliser pour classer les éléments. Le troisième constructeur spécifie explicitement le type d’allocateur ( `Al`) à utiliser. Le mot clé `explicit` supprime certains genres de conversions de type automatiques.  
  
 Le quatrième constructeur spécifie une copie de la classe map `Right`.  
  
 Le cinquième constructeur spécifie une copie de la classe map en déplaçant `Right`.  
  
 Le sixième, le septième et le huitième constructeurs utilisent une initializer_list à partir de laquelle copier les membres.  
  
 Les trois constructeurs suivants copient la plage `[First, Last)` d’une classe map avec un caractère explicite croissant en ce qui concerne la spécification du type de fonction de comparaison de la classe `Traits` et de l’allocateur.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// map_map.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    typedef pair <int, int> Int_Pair;  
    map <int, int>::iterator m1_Iter, m3_Iter, m4_Iter, m5_Iter, m6_Iter, m7_Iter;  
    map <int, int, less<int> >::iterator m2_Iter;  
  
    // Create an empty map m0 of key type integer  
    map <int, int> m0;  
  
    // Create an empty map m1 with the key comparison  
    // function of less than, then insert 4 elements  
    map <int, int, less<int> > m1;  
    m1.insert(Int_Pair(1, 10));  
    m1.insert(Int_Pair(2, 20));  
    m1.insert(Int_Pair(3, 30));  
    m1.insert(Int_Pair(4, 40));  
  
    // Create an empty map m2 with the key comparison  
    // function of geater than, then insert 2 elements  
    map <int, int, less<int> > m2;  
    m2.insert(Int_Pair(1, 10));  
    m2.insert(Int_Pair(2, 20));  
  
    // Create a map m3 with the   
    // allocator of map m1  
    map <int, int>::allocator_type m1_Alloc;  
    m1_Alloc = m1.get_allocator();  
    map <int, int> m3(less<int>(), m1_Alloc);  
    m3.insert(Int_Pair(3, 30));  
  
    // Create a copy, map m4, of map m1  
    map <int, int> m4(m1);  
  
    // Create a map m5 by copying the range m1[ first,  last)  
    map <int, int>::const_iterator m1_bcIter, m1_ecIter;  
    m1_bcIter = m1.begin();  
    m1_ecIter = m1.begin();  
    m1_ecIter++;  
    m1_ecIter++;  
    map <int, int> m5(m1_bcIter, m1_ecIter);  
  
    // Create a map m6 by copying the range m4[ first,  last)  
    // and with the allocator of map m2  
    map <int, int>::allocator_type m2_Alloc;  
    m2_Alloc = m2.get_allocator();  
    map <int, int> m6(m4.begin(), ++m4.begin(), less<int>(), m2_Alloc);  
  
    cout << "m1 =";  
    for (auto i : m1)  
        cout << i.first << " " << i.second << ", ";  
    cout << endl;  
  
    cout << "m2 =";  
    for(auto i : m2)  
        cout << i.first << " " << i.second << ", ";  
    cout << endl;  
  
    cout << "m3 =";  
    for (auto i : m3)  
        cout << i.first << " " << i.second << ", ";  
    cout << endl;  
  
    cout << "m4 =";  
    for (auto i : m4)  
        cout << i.first << " " << i.second << ", ";  
    cout << endl;  
  
    cout << "m5 =";  
    for (auto i : m5)  
        cout << i.first << " " << i.second << ", ";  
    cout << endl;  
  
    cout << "m6 =";  
    for (auto i : m6)  
        cout << i.first << " " << i.second << ", ";  
    cout << endl;  
  
    // Create a map m7 by moving m5  
    cout << "m7 =";  
    map<int, int> m7(move(m5));  
    for (auto i : m7)  
        cout << i.first << " " << i.second << ", ";  
    cout << endl;  
  
    // Create a map m8 by copying in an initializer_list  
    map<int, int> m8{ { { 1, 1 }, { 2, 2 }, { 3, 3 }, { 4, 4 } } };  
    cout << "m8: = ";  
    for (auto i : m8)  
        cout << i.first << " " << i.second << ", ";  
    cout << endl;  
  
    // Create a map m9 with an initializer_list and a comparator  
    map<int, int> m9({ { 5, 5 }, { 6, 6 }, { 7, 7 }, { 8, 8 } }, less<int>());  
    cout << "m9: = ";  
    for (auto i : m9)  
        cout << i.first << " " << i.second << ", ";  
    cout << endl;  
  
    // Create a map m10 with an initializer_list, a comparator, and an allocator  
    map<int, int> m10({ { 9, 9 }, { 10, 10 }, { 11, 11 }, { 12, 12 } }, less<int>(), m9.get_allocator());  
    cout << "m10: = ";  
    for (auto i : m10)  
        cout << i.first << " " << i.second << ", ";  
    cout << endl;  
}  
  
```  
  
##  <a name="mapped_type"></a>  map::mapped_type  
 Type qui représente le type de données stocké dans une classe map.  
  
```  
typedef Type mapped_type;  
```  
  
### <a name="remarks"></a>Notes  
 Le type `mapped_type` est un synonyme du paramètre de modèle `Type` de la classe.  
  
 Pour plus d’informations sur `Type`, consultez la rubrique [map, classe](../standard-library/map-class.md).  
  
### <a name="example"></a>Exemple  
  Pour découvrir comment déclarer et utiliser `mapped_type`, consultez l’exemple relatif à [value_type](#value_type).  
  
##  <a name="max_size"></a>  map::max_size  
 Retourne la longueur maximale de la classe map.  
  
```  
size_type max_size() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Longueur maximale autorisée de la classe map.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// map_max_size.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map <int, int> m1;  
   map <int, int> :: size_type i;  
  
   i = m1.max_size( );  
   cout << "The maximum possible length "  
        << "of the map is " << i << "."  
        << endl << "(Magnitude is machine specific.)";  
}  
```  
  
##  <a name="op_at"></a>  map::operator[]  
 Insère un élément dans une classe map avec une valeur de clé spécifiée.  
  
```  
Type& operator[](const Key& key);

Type& operator[](Key&& key);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|`key`|Valeur de clé de l’élément à insérer.|  
  
### <a name="return-value"></a>Valeur de retour  
 Référence à la valeur de données de l'élément inséré.  
  
### <a name="remarks"></a>Notes  
 Si la valeur de clé d’argument est introuvable, elle est insérée avec la valeur par défaut du type de données.  
  
 `operator[]` peut être utilisé pour insérer des éléments dans une classe map `m` en utilisant `m[ key] = DataValue;` ; où `DataValue` est la valeur du `mapped_type` de l’élément avec une valeur de clé de `key`.  
  
 Lorsque vous utilisez `operator[]` pour insérer des éléments, la référence retournée n'indique pas si l'insertion va modifier un élément existant ou en créer un nouveau. Les fonctions membres [find](#find) et [insert](#insert) peuvent être utilisées pour déterminer si un élément avec une clé spécifiée est déjà présent avant une insertion.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// map_op_insert.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
#include <string>  
  
int main( )  
{  
   using namespace std;  
   typedef pair <const int, int> cInt2Int;  
   map <int, int> m1;  
   map <int, int> :: iterator pIter;  
  
   // Insert a data value of 10 with a key of 1  
   // into a map using the operator[] member function  
   m1[ 1 ] = 10;  
  
   // Compare other ways to insert objects into a map  
   m1.insert ( map <int, int> :: value_type ( 2, 20 ) );  
   m1.insert ( cInt2Int ( 3, 30 ) );  
  
   cout  << "The keys of the mapped elements are:";  
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )  
      cout << " " << pIter -> first;  
   cout << "." << endl;  
  
   cout  << "The values of the mapped elements are:";  
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )  
      cout << " " << pIter -> second;  
   cout << "." << endl;  
  
   // If the key already exists, operator[]  
   // changes the value of the datum in the element  
   m1[ 2 ] = 40;  
  
   // operator[] will also insert the value of the data  
   // type's default constructor if the value is unspecified  
   m1[5];  
  
   cout  << "The keys of the mapped elements are now:";  
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )  
      cout << " " << pIter -> first;  
   cout << "." << endl;  
  
   cout  << "The values of the mapped elements are now:";  
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )  
      cout << " " << pIter -> second;  
   cout << "." << endl;  
  
// insert by moving key  
    map<string, int> c2;  
    string str("abc");  
    cout << "c2[move(str)] == " << c2[move(str)] << endl;  
    cout << "c2["abc"] == " << c2["abc"] << endl;  
  
    return (0);   
}  
```  
  
```Output  
The keys of the mapped elements are: 1 2 3.  
The values of the mapped elements are: 10 20 30.  
The keys of the mapped elements are now: 1 2 3 5.  
The values of the mapped elements are now: 10 40 30 0.  
c2[move(str)] == 0  
c2["abc"] == 1  
```  
  
##  <a name="op_eq"></a>  map::operator=  
 Remplace les éléments d'une classe map par une copie d'une autre classe map.  
  
```  
map& operator=(const map& right);

map& operator=(map&& right);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|`right`|[map](../standard-library/map-class.md) copié dans le `map`.|  
  
### <a name="remarks"></a>Notes  
 Après avoir supprimé les éléments existants dans un objet `map`, `operator=` copie ou déplace le contenu de `right` dans la classe map.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// map_operator_as.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
   {  
   using namespace std;  
   map<int, int> v1, v2, v3;  
   map<int, int>::iterator iter;  
  
   v1.insert(pair<int, int>(1, 10));  
  
   cout << "v1 = " ;  
   for (iter = v1.begin(); iter != v1.end(); iter++)  
      cout << iter->second << " ";  
   cout << endl;  
  
   v2 = v1;  
   cout << "v2 = ";  
   for (iter = v2.begin(); iter != v2.end(); iter++)  
      cout << iter->second << " ";  
   cout << endl;  
  
// move v1 into v2  
   v2.clear();  
   v2 = move(v1);  
   cout << "v2 = ";  
   for (iter = v2.begin(); iter != v2.end(); iter++)  
      cout << iter->second << " ";  
   cout << endl;  
   }  
```  
  
##  <a name="pointer"></a>  map::pointer  
 Type qui fournit un pointeur vers un élément d’une classe map.  
  
```  
typedef typename allocator_type::pointer pointer;  
```  
  
### <a name="remarks"></a>Notes  
 Un type **pointer** peut être utilisé pour modifier la valeur d’un élément.  
  
 Dans la plupart des cas, vous devez utiliser un [iterator](#iterator) pour accéder aux éléments dans un objet map.  
  
##  <a name="rbegin"></a>  map::rbegin  
 Retourne un itérateur qui traite le premier élément d’une classe map inversée.  
  
```  
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Itérateur bidirectionnel inversé qui traite le premier élément d’une classe map inversée ou qui traite ce qui était le dernier élément de la classe map non inversée.  
  
### <a name="remarks"></a>Notes  
 `rbegin` est utilisé avec une classe map inversée comme [begin](#begin) est utilisé avec une classe map.  
  
 Si la valeur de retour de `rbegin` est assignée à un `const_reverse_iterator`, l’objet map ne peut pas être changé. Si la valeur de retour de `rbegin` est assignée à un `reverse_iterator`, l’objet map peut être changé.  
  
 Vous pouvez utiliser `rbegin` pour itérer une classe map vers l’arrière.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// map_rbegin.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   map <int, int> m1;  
  
   map <int, int> :: iterator m1_Iter;  
   map <int, int> :: reverse_iterator m1_rIter;  
   map <int, int> :: const_reverse_iterator m1_crIter;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 1, 10 ) );  
   m1.insert ( Int_Pair ( 2, 20 ) );  
   m1.insert ( Int_Pair ( 3, 30 ) );  
  
   m1_rIter = m1.rbegin( );  
   cout << "The first element of the reversed map m1 is "  
        << m1_rIter -> first << "." << endl;  
  
   // begin can be used to start an iteration   
   // through a map in a forward order  
   cout << "The map is: ";  
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)  
      cout << m1_Iter -> first << " ";  
      cout << "." << endl;  
  
   // rbegin can be used to start an iteration   
   // through a map in a reverse order  
   cout << "The reversed map is: ";  
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)  
      cout << m1_rIter -> first << " ";  
      cout << "." << endl;  
  
   // A map element can be erased by dereferencing to its key   
   m1_rIter = m1.rbegin( );  
   m1.erase ( m1_rIter -> first );  
  
   m1_rIter = m1.rbegin( );  
   cout << "After the erasure, the first element "  
        << "in the reversed map is "  
        << m1_rIter -> first << "." << endl;  
}  
```  
  
```Output  
The first element of the reversed map m1 is 3.  
The map is: 1 2 3 .  
The reversed map is: 3 2 1 .  
After the erasure, the first element in the reversed map is 2.  
```  
  
##  <a name="reference"></a>  map::reference  
 Type qui fournit une référence à un élément stocké dans une classe map.  
  
```  
typedef typename allocator_type::reference reference;  
```  
  
### <a name="example"></a>Exemple  
  
```cpp  
// map_reference.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map <int, int> m1;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 1, 10 ) );  
   m1.insert ( Int_Pair ( 2, 20 ) );  
  
   // Declare and initialize a const_reference &Ref1   
   // to the key of the first element  
   const int &Ref1 = ( m1.begin( ) -> first );  
  
   // The following line would cause an error because the   
   // non-const_reference cannot be used to access the key  
   // int &Ref1 = ( m1.begin( ) -> first );  
  
   cout << "The key of first element in the map is "  
        << Ref1 << "." << endl;  
  
   // Declare and initialize a reference &Ref2   
   // to the data value of the first element  
   int &Ref2 = ( m1.begin( ) -> second );  
  
   cout << "The data value of first element in the map is "  
        << Ref2 << "." << endl;  
  
   //The non-const_reference can be used to modify the   
   //data value of the first element  
   Ref2 = Ref2 + 5;  
   cout << "The modified data value of first element is "  
        << Ref2 << "." << endl;  
}  
```  
  
```Output  
The key of first element in the map is 1.  
The data value of first element in the map is 10.  
The modified data value of first element is 15.  
```  
  
##  <a name="rend"></a>  map::rend  
 Retourne un itérateur qui traite l’emplacement suivant le dernier élément d’une classe map inversée.  
  
```  
const_reverse_iterator rend() const;

reverse_iterator rend();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Itérateur bidirectionnel inversé qui traite l’emplacement qui suit le dernier élément d’une classe map inversée (emplacement qui précédait le premier élément de la classe map non inversée).  
  
### <a name="remarks"></a>Notes  
 `rend` est utilisé avec une classe map inversée de la même manière que [end](#end) est utilisé avec une classe map.  
  
 Si la valeur de retour de `rend` est assignée à un `const_reverse_iterator`, l’objet map ne peut pas être changé. Si la valeur de retour de `rend` est assignée à un `reverse_iterator`, l’objet map peut être changé.  
  
 Vous pouvez utiliser `rend` pour déterminer si un itérateur inversé a atteint la fin de sa classe map.  
  
 La valeur retournée par `rend` ne doit pas être déréférencée.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// map_rend.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map <int, int> m1;  
  
   map <int, int> :: iterator m1_Iter;  
   map <int, int> :: reverse_iterator m1_rIter;  
   map <int, int> :: const_reverse_iterator m1_crIter;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 1, 10 ) );  
   m1.insert ( Int_Pair ( 2, 20 ) );  
   m1.insert ( Int_Pair ( 3, 30 ) );  
  
   m1_rIter = m1.rend( );  
   m1_rIter--;  
   cout << "The last element of the reversed map m1 is "  
        << m1_rIter -> first << "." << endl;  
  
   // begin can be used to start an iteration   
   // through a map in a forward order  
   cout << "The map is: ";  
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)  
      cout << m1_Iter -> first << " ";  
      cout << "." << endl;  
  
   // rbegin can be used to start an iteration   
   // through a map in a reverse order  
   cout << "The reversed map is: ";  
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)  
      cout << m1_rIter -> first << " ";  
      cout << "." << endl;  
  
   // A map element can be erased by dereferencing to its key   
   m1_rIter = --m1.rend( );  
   m1.erase ( m1_rIter -> first );  
  
   m1_rIter = m1.rend( );  
   m1_rIter--;  
   cout << "After the erasure, the last element "  
        << "in the reversed map is "  
        << m1_rIter -> first << "." << endl;  
}  
```  
  
```Output  
The last element of the reversed map m1 is 1.  
The map is: 1 2 3 .  
The reversed map is: 3 2 1 .  
After the erasure, the last element in the reversed map is 2.  
```  
  
##  <a name="reverse_iterator"></a>  map::reverse_iterator  
 Type qui fournit un itérateur bidirectionnel capable de lire ou de modifier tout élément d’une classe map inversée.  
  
```  
typedef std::reverse_iterator<iterator> reverse_iterator;  
```  
  
### <a name="remarks"></a>Notes  
 Un type `reverse_iterator` ne peut pas changer la valeur d’un élément. Il sert à itérer la classe map dans l’ordre inverse.  
  
 Le `reverse_iterator` défini par la classe map pointe vers des éléments qui sont des objets de [value_type](#value_type), qui est de type `pair`*\<***constKey**, **Type***>*, dont le premier membre est la clé de l’élément et dont le deuxième membre est la référence mappée détenue par l’élément.  
  
 Pour déréférencer un `reverse_iterator` `rIter` pointe sur un élément dans un mappage, utilisez le  **->**  opérateur.  
  
 Pour accéder à la valeur de la clé de l’élément, utilisez `rIter` -> **first**, ce qui équivaut à (\* `rIter`). **first**. Pour accéder à la valeur de la référence mappée de l’élément, utilisez `rIter` -> **second**, ce qui équivaut à (\* `rIter`). **first**.  
  
### <a name="example"></a>Exemple  
  Pour découvrir comment déclarer et utiliser `reverse_iterator`, consultez l’exemple relatif à [rbegin](#rbegin).  
  
##  <a name="size"></a>  map::size  
 Retourne le nombre d'éléments d'une classe map.  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Longueur actuelle du map.  
  
### <a name="example"></a>Exemple  
  L'exemple suivant illustre l'utilisation de la fonction membre map::size.  
  
```  
// map_size.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    map<int, int> m1, m2;  
    map<int, int>::size_type i;  
    typedef pair<int, int> Int_Pair;  
  
    m1.insert(Int_Pair(1, 1));  
    i = m1.size();  
    cout << "The map length is " << i << "." << endl;  
  
    m1.insert(Int_Pair(2, 4));  
    i = m1.size();  
    cout << "The map length is now " << i << "." << endl;  
}  
```  
  
```Output  
The map length is 1.  
The map length is now 2.  
```  
  
##  <a name="size_type"></a>  map::size_type  
 Type entier non signé qui peut représenter le nombre d’éléments d’une classe map.  
  
```  
typedef typename allocator_type::size_type size_type;  
```  
  
### <a name="example"></a>Exemple  
  Pour savoir comment déclarer et utiliser `size_type`, consultez l’exemple relatif à [size](#size).  
  
##  <a name="swap"></a>  map::swap  
 Échange les éléments de deux classes map.  
  
```  
void swap(
    map<Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Paramètres  
 `right`  
 Argument map qui fournit les éléments à échanger avec la classe map cible.  
  
### <a name="remarks"></a>Notes  
 La fonction membre n’invalide aucun pointeur, itérateur ou référence qui désigne des éléments dans les deux classes map dont les éléments sont échangés.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// map_swap.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map <int, int> m1, m2, m3;  
   map <int, int>::iterator m1_Iter;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 1, 10 ) );  
   m1.insert ( Int_Pair ( 2, 20 ) );  
   m1.insert ( Int_Pair ( 3, 30 ) );  
   m2.insert ( Int_Pair ( 10, 100 ) );  
   m2.insert ( Int_Pair ( 20, 200 ) );  
   m3.insert ( Int_Pair ( 30, 300 ) );  
  
   cout << "The original map m1 is:";  
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )  
      cout << " " << m1_Iter -> second;  
   cout   << "." << endl;  
  
   // This is the member function version of swap  
   //m2 is said to be the argument map; m1 the target map  
   m1.swap( m2 );  
  
   cout << "After swapping with m2, map m1 is:";  
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )  
      cout << " " << m1_Iter -> second;  
   cout  << "." << endl;  
  
   // This is the specialized template version of swap  
   swap( m1, m3 );  
  
   cout << "After swapping with m3, map m1 is:";  
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )  
      cout << " " << m1_Iter -> second;  
   cout   << "." << endl;  
}  
```  
  
```Output  
The original map m1 is: 10 20 30.  
After swapping with m2, map m1 is: 100 200.  
After swapping with m3, map m1 is: 300.  
```  
  
##  <a name="upper_bound"></a>  map::upper_bound  
 Retourne un itérateur pointant vers le premier élément d’une classe map qui a une valeur de clé supérieure à celle d’une clé spécifiée.  
  
```  
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `key`  
 Valeur de clé d’argument à comparer à la valeur de clé de tri d’un élément de la classe map dans laquelle la recherche est effectuée.  
  
### <a name="return-value"></a>Valeur de retour  
 **iterator** ou `const_iterator` qui traite l’emplacement d’un élément dans une classe map ayant une clé supérieure à la clé d’argument, ou qui traite l’emplacement suivant le dernier élément dans la classe map si aucune correspondance n’est trouvée pour la clé.  
  
 Si la valeur de retour est assignée à un `const_iterator`, l’objet map ne peut pas être changé. Si la valeur de retour est assignée à un **iterator**, l’objet map peut être changé.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// map_upper_bound.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map <int, int> m1;  
   map <int, int> :: const_iterator m1_AcIter, m1_RcIter;  
   typedef pair <int, int> Int_Pair;  
  
   m1.insert ( Int_Pair ( 1, 10 ) );  
   m1.insert ( Int_Pair ( 2, 20 ) );  
   m1.insert ( Int_Pair ( 3, 30 ) );  
  
   m1_RcIter = m1.upper_bound( 2 );  
   cout << "The first element of map m1 with a key "  
        << "greater than 2 is: "  
        << m1_RcIter -> second << "." << endl;  
  
   // If no match is found for the key, end is returned  
   m1_RcIter = m1. upper_bound ( 4 );  
  
   if ( m1_RcIter == m1.end( ) )  
      cout << "The map m1 doesn't have an element "  
           << "with a key greater than 4." << endl;  
   else  
      cout << "The element of map m1 with a key > 4 is: "  
           << m1_RcIter -> second << "." << endl;  
  
   // The element at a specific location in the map can be found   
   // using a dereferenced iterator addressing the location  
   m1_AcIter = m1.begin( );  
   m1_RcIter = m1. upper_bound ( m1_AcIter -> first );  
   cout << "The 1st element of m1 with a key greater than\n"  
        << "that of the initial element of m1 is: "  
        << m1_RcIter -> second << "." << endl;  
}  
```  
  
```Output  
The first element of map m1 with a key greater than 2 is: 30.  
The map m1 doesn't have an element with a key greater than 4.  
The 1st element of m1 with a key greater than  
that of the initial element of m1 is: 20.  
```  
  
##  <a name="value_comp"></a>  map::value_comp  
 La fonction membre retourne un objet de fonction qui détermine l’ordre des éléments d’une classe map en comparant leurs valeurs de clés.  
  
```  
value_compare value_comp() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne l’objet de fonction de comparaison utilisé par une classe map pour ordonner ses éléments.  
  
### <a name="remarks"></a>Notes  
 Pour une classe map *m*, si deux éléments *e*1( *k*1, *d*1) et *e*2( *k*2, `d`2) sont des objets de type `value_type`, où *k*1 et *k*2 ont des clés de type `key_type` et `d`1 et `d`2 ont des données de type `mapped_type`, alors *m.*`value_comp`( *e*1, *e*2) équivaut à *m.*`key_comp`*(k*1, *k*2). Un objet stocké définit la fonction membre  
  
 **opérateur bool**( **value_type &**`left`, **value_type &**`right`) ;  
  
 qui retourne **true** si la valeur de clé de `left` précède et n’est pas égale à la valeur clé de `right` dans l’ordre de tri.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// map_value_comp.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   map <int, int, less<int> > m1;  
   map <int, int, less<int> >::value_compare vc1 = m1.value_comp( );  
   pair< map<int,int>::iterator, bool > pr1, pr2;  
  
   pr1= m1.insert ( map <int, int> :: value_type ( 1, 10 ) );  
   pr2= m1.insert ( map <int, int> :: value_type ( 2, 5 ) );  
  
   if( vc1( *pr1.first, *pr2.first ) == true )     
   {  
      cout << "The element ( 1,10 ) precedes the element ( 2,5 )."  
           << endl;  
   }  
   else     
   {  
      cout << "The element ( 1,10 ) does not precede the element ( 2,5 )."  
           << endl;  
   }  
  
   if(vc1( *pr2.first, *pr1.first ) == true )  
   {  
      cout << "The element ( 2,5 ) precedes the element ( 1,10 )."  
           << endl;  
   }  
   else     
   {  
      cout << "The element ( 2,5 ) does not precede the element ( 1,10 )."  
           << endl;  
   }  
}  
```  
  
```Output  
The element ( 1,10 ) precedes the element ( 2,5 ).  
The element ( 2,5 ) does not precede the element ( 1,10 ).  
```  
  
##  <a name="value_type"></a>  map::value_type  
 Type de l’objet stocké comme élément dans une classe map.  
  
```  
typedef pair<const Key, Type> value_type;  
```  
  
### <a name="example"></a>Exemple  
  
```cpp  
// map_value_type.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   typedef pair <const int, int> cInt2Int;  
   map <int, int> m1;  
   map <int, int> :: key_type key1;  
   map <int, int> :: mapped_type mapped1;  
   map <int, int> :: value_type value1;  
   map <int, int> :: iterator pIter;  
  
   // value_type can be used to pass the correct type  
   // explicitly to avoid implicit type conversion  
   m1.insert ( map <int, int> :: value_type ( 1, 10 ) );  
  
   // Compare other ways to insert objects into a map  
   m1.insert ( cInt2Int ( 2, 20 ) );  
   m1[ 3 ] = 30;  
  
   // Initializing key1 and mapped1  
   key1 = ( m1.begin( ) -> first );  
   mapped1 = ( m1.begin( ) -> second );  
  
   cout << "The key of first element in the map is "  
        << key1 << "." << endl;  
  
   cout << "The data value of first element in the map is "  
        << mapped1 << "." << endl;  
  
   // The following line would cause an error because  
   // the value_type is not assignable  
   // value1 = cInt2Int ( 4, 40 );  
  
   cout  << "The keys of the mapped elements are:";  
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )  
      cout << " " << pIter -> first;  
   cout << "." << endl;  
  
   cout  << "The values of the mapped elements are:";  
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )  
      cout << " " << pIter -> second;  
   cout << "." << endl;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [\<map>, membres](http://msdn.microsoft.com/en-us/7e8f0bc2-6034-40f6-9d14-76d4cef86308)   
 [Conteneurs](../cpp/containers-modern-cpp.md)   
 [Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)

