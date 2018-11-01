---
title: Collections (C++/CX)
ms.date: 01/22/2017
ms.assetid: 914da30b-aac5-4cd7-9da3-a5ac08cdd72c
ms.openlocfilehash: d139bcfc6cdf61940a40ca069dd157c1805e2034
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531587"
---
# <a name="collections-ccx"></a>Collections (C++/CX)

En C / c++ / programme CX, vous pouvez utiliser librement les conteneurs de bibliothèque STL (Standard Template Library), ou tout autre type de collection défini par l’utilisateur. Toutefois, lorsque vous passez des collections dans les deux sens entre l’interface binaire d’application Windows Runtime (ABI), par exemple, pour un contrôle XAML ou à un client JavaScript, vous devez utiliser des types de collections Windows Runtime.

Le Runtime Windows définit les interfaces pour les collections et les types associés et C++ / c++ / CX fournit les implémentations C++ concrètes dans le fichier d’en-tête collection.h. Cette illustration montre les relations entre les types de collection :

![C&#43;&#43;&#47;l’arborescence d’héritage pour les types de collection CX](../cppcx/media/cppcxcollectionsinheritancetree.png "CPPCXCollectionsInheritanceTree")

- La [classe Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) ressemble à la [classe std::vector](../standard-library/vector-class.md).

- La [classe Platform::Collections::Map](../cppcx/platform-collections-map-class.md) ressemble à la [classe std::map](../standard-library/map-class.md).

- La[classe Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md) et la[classe Platform::Collections::MapView](../cppcx/platform-collections-mapview-class.md) sont des versions en lecture seule de `Vector` et la `Map`.

- Les itérateurs sont définis dans [Platform::Collections Namespace](../cppcx/platform-collections-namespace.md). Ces itérateurs répondent aux spécifications des itérateurs STL et permettent d’utiliser [std::find](../standard-library/algorithm-functions.md#find),  [std::count_if](../standard-library/algorithm-functions.md#count_if)et d’autres algorithmes STL sur n’importe quel type d’interface [Windows::Foundation::Collections](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.aspx) ou type concret [Platform::Collections](../cppcx/platform-collections-namespace.md) . Par exemple, cela signifie que vous pouvez itérer une collection dans un composant Windows Runtime qui est créé en c# et lui applique un algorithme STL.

   > [!IMPORTANT]
   > Les itérateurs de proxy `VectorIterator` et `VectorViewIterator` utilisent les objets proxy `VectoryProxy<T>` et `ArrowProxy<T>` pour activer l'utilisation avec des conteneurs STL. Pour plus d'informations, consultez « Éléments VectorProxy » dans la suite de cet article.

- C++ / c++ / prise en charge les mêmes garanties de sécurité que les conteneurs STL prennent en charge des types de collection de CX.

- [Windows::Foundation::Collections::IObservableVector](/uwp/api/Windows.Foundation.Collections.IObservableVector_T_) et [Windows::Foundation::Collections::IObservableMap](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_) définissent des événements qui sont déclenchés quand la collection est modifiée de différentes manières. En implémentant ces interfaces,  [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) et [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) prennent en charge la liaison de données avec les collections XAML. Par exemple, si vous avez un vecteur `Vector` qui est lié aux données à un `Grid`, lorsque vous ajoutez un élément à une collection, la modification est répercutée dans la grille de l'interface utilisateur.

## <a name="vector-usage"></a>Utilisation de Vector

Lorsque votre classe doit passer un conteneur de séquence à un autre composant Windows Runtime, utilisez [Windows::Foundation :: Collections :: IVector\<T >](https://msdn.microsoft.com/library/windows/apps/br206631.aspx) comme paramètre ou type de retour, et [plateforme :: Collections::Vector\<T >](../cppcx/platform-collections-vector-class.md) comme implémentation concrète. Si vous tentez d'utiliser un type `Vector` dans une valeur ou un paramètre de retour, l'erreur de compilateur C3986 est générée. Vous pouvez corriger l'erreur en remplaçant le `Vector` par un `IVector`.

> [!IMPORTANT]
> Si vous passez une séquence dans le cadre de votre propre programme, utilisez `Vector` ou `std::vector` car ils sont plus efficaces que `IVector`. Utilisez `IVector` uniquement lorsque vous passez le conteneur à travers l'ABI.
>
> Le système de type Windows Runtime ne prend pas en charge le concept des tableaux en escalier et par conséquent, vous ne pouvez pas utiliser un IVector < Platform::Array\<T >> comme paramètre de méthode ou de la valeur de retour. Pour passer un tableau en escalier ou une séquence de séquences à travers l'ABI, utilisez `IVector<IVector<T>^>`.

`Vector<T>` fournit les méthodes requises pour ajouter, supprimer les éléments et y accéder dans la collection, et il est implicitement convertible en `IVector<T>`. Vous pouvez également utiliser les algorithmes STL sur les instances de `Vector<T>`. L'exemple ci-dessous illustre l'utilisation de base. Les fonctions [begin](../cppcx/begin-function.md) et [end](../cppcx/end-function.md) sont issues ici de l'espace `Platform::Collections` au lieu de l'espace `std` .

[!code-cpp[cx_collections#01](../cppcx/codesnippet/CPP/collections/class1.cpp#01)]

Si vous avez du code existant qui utilise `std::vector` et que vous souhaitez réutiliser dans un composant Windows Runtime, utilisez simplement une de la `Vector` constructeurs qui prend une `std::vector` ou une paire d’itérateurs pour construire un `Vector` au point où vous passez le collection travers l’ABI. L'exemple ci-dessous indique comment utiliser le constructeur de déplacement `Vector` pour une initialisation efficace à partir d'un `std::vector`. Une fois l'opération de déplacement terminée, la variable `vec` d'origine n'est plus valide.

[!code-cpp[cx_collections#02](../cppcx/codesnippet/CPP/collections/class1.cpp#02)]

Si vous avez un vecteur de chaînes que vous devez passer à travers l'ABI à un futur point, vous devez décider s'il faut créer des chaînes initialement en tant que types `std::wstring` ou `Platform::String^` . Si vous devez effectuer un important traitement sur les chaînes, utilisez `wstring`. Sinon, créez les chaînes en tant que types `Platform::String^` et évitez ainsi d'avoir à les convertir ultérieurement. Vous devez également décider s'il faut placer ces chaînes dans `std:vector` ou `Platform::Collections::Vector` en interne. De manière générale, utilisez `std::vector` et créez ensuite `Platform::Vector` à partir de ce dernier uniquement lorsque vous passez le conteneur à travers l'ABI.

## <a name="value-types-in-vector"></a>Types de valeur relatifs au vecteur

Tout élément à stocker dans [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) doit prendre en charge la comparaison d'égalité, implicitement ou à l'aide d'un comparateur [std::equal_to](../standard-library/equal-to-struct.md) personnalisé que vous fournissez. Tous les types de références et tous les types scalaires prennent en charge implicitement les comparaisons d'égalité. Pour les types de valeurs non scalaires tels que [Windows::Foundation::DateTime](https://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx), ou pour les comparaisons personnalisées, par exemple, `objA->UniqueID == objB->UniqueID`, vous devez fournir un objet de fonction personnalisé.

## <a name="vectorproxy-elements"></a>Éléments VectorProxy

[Platform::Collections :: vectoriterator](../cppcx/platform-collections-vectoriterator-class.md) et [Platform::Collections :: vectorviewiterator](../cppcx/platform-collections-vectorviewiterator-class.md) activer l’utilisation de `range for` boucles et des algorithmes comme [std::sort](../standard-library/algorithm-functions.md#sort) avec un [ IVector\<T >](https://msdn.microsoft.com/library/windows/apps/br206631.aspx) conteneur. Toutefois, les éléments `IVector` ne sont pas accessibles par l’intermédiaire du déréférencement de pointeur C++. Ils sont accessibles uniquement avec les méthodes [GetAt](https://msdn.microsoft.com/library/windows/apps/br206634.aspx) et [SetAt](https://msdn.microsoft.com/library/windows/apps/br206642.aspx) . Par conséquent, ces itérateurs utilisent les classes proxy `Platform::Details::VectorProxy<T>` et `Platform::Details::ArrowProxy<T>` pour fournir l’accès aux éléments individuels via __\*__, __->__ et  __\[]__ opérateurs, comme requis par la bibliothèque Standard. À proprement parler, avec un `IVector<Person^> vec`, le type de `*begin(vec)` est `VectorProxy<Person^>`. Toutefois, l'objet proxy est presque toujours transparent pour votre code. Ces objets proxy ne sont pas documentés car ils servent uniquement à un usage interne par les itérateurs, mais il est utile de savoir comment le mécanisme fonctionne.

Lorsque vous utilisez une boucle `range for` sur les conteneurs `IVector` , utilisez `auto&&` pour permettre à la variable d'itérateur d'effectuer une liaison correcte avec les éléments `VectorProxy` . Si vous utilisez `auto` ou `auto&`, l'avertissement de compilateur C4239 est déclenché et `VectoryProxy` est mentionné dans le texte d'avertissement.

L'illustration suivante montre une boucle `range for` sur un `IVector<Person^>`. Notez que l'exécution est interrompue sur le point d'arrêt à la ligne 64. La fenêtre **Espion express** indique que la variable d'itérateur `p` est en fait un `VectorProxy<Person^>` qui a les variables membres `m_v` et `m_i` . Toutefois, lorsque vous appelez la méthode `GetType` sur cette variable, elle retourne le type identique à l'instance `Person` `p2`. Le principal avantage est que, bien que `VectorProxy` et `ArrowProxy` puissent apparaître dans **Espion express**, le débogueur de certaines erreurs de compilateur, il n'est pas nécessaire en général de coder explicitement pour eux.

![VectorProxy dans une plage&#45;en boucle for](../cppcx/media/vectorproxy-1.png "VectorProxy_1")

Un scénario dans lequel vous devez coder autour de l'objet proxy est lorsque vous devez effectuer un `dynamic_cast` sur les éléments, par exemple lorsque vous recherchez des objets XAML d'un type particulier dans une collection d'éléments `UIElement` . Dans ce cas, vous devez commencer par caster l'élément en [Platform::Object](../cppcx/platform-object-class.md)puis effectuer le cast dynamique :

```cpp
void FindButton(UIElementCollection^ col)
{
    // Use auto&& to avoid warning C4239
    for (auto&& elem : col)
    {
        Button^ temp = dynamic_cast<Button^>(static_cast<Object^>(elem));
        if (nullptr != temp)
        {
            // Use temp...
        }
    }
}
```

## <a name="map-usage"></a>Utilisation de Map

Cet exemple montre comment insérer des éléments et les consulter dans un [Platform::Collections :: Map](../cppcx/platform-collections-map-class.md), puis retourner le `Map` comme un en lecture seule [Windows::Foundation::Collections::IMapView] / uwp/api / Type de Windows.Foundation.Collections.IMapView_K_V_).

[!code-cpp[cx_collections#04](../cppcx/codesnippet/CPP/collections/class1.cpp#04)]

En général, pour les fonctionnalités de carte intégrées, préférez le type `std::map` pour des raisons de performance. Si vous devez passer le conteneur à travers l’ABI, construisez un [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) à partir de [std::map](../standard-library/map-class.md) et retournez le `Map` sous forme de [Windows::Foundation::Collections::IMap](/uwp/api/Windows.Foundation.Collections.IMap_K_V_). Si vous tentez d'utiliser un type `Map` dans une valeur ou un paramètre de retour, l'erreur de compilateur C3986 est générée. Vous pouvez corriger l'erreur en remplaçant le `Map` par un `IMap`. Dans certains cas, par exemple si vous n'effectuez pas un grand nombre de recherches ou d'insertions et que vous passez fréquemment la collection à travers l'ABI, il peut être moins coûteux d'utiliser `Platform::Collections::Map` et d'éviter ainsi le coût de conversion de `std::map`. Dans tous les cas, évitez les recherches et insertions sur un `IMap` , car c'est le moins performant des trois types. Effectuez une conversion en `IMap` uniquement au point où vous passez le conteneur à travers l'ABI.

## <a name="value-types-in-map"></a>Types de valeur relatifs au mappage

Les éléments contenus dans [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) sont classés. Tout élément à stocker dans `Map` doit prendre en charge la comparaison « inférieur à » avec le classement faible strict, implicitement ou à l'aide d'un comparateur personnalisé [stl::less](../standard-library/less-struct.md) que vous fournissez. Les types scalaires prennent en charge la comparaison implicitement. Pour les types de valeurs non scalaires tels que `Windows::Foundation::DateTime`, ou pour les comparaisons personnalisées, par exemple, `objA->UniqueID < objB->UniqueID`, vous devez fournir un comparateur personnalisé.

## <a name="collection-types"></a>Types de collections

Les collections sont classées en quatre catégories : versions modifiables et versions en lecture seule des collections séquentielles et associatives. En outre, C++ / c++ / CX améliore les collections en fournissant trois classes d’itérateur qui simplifient l’accès aux collections.

Les éléments d'une collection modifiable peuvent être modifiés, mais les éléments d'une collection en lecture seule, appelée *vue*, peuvent uniquement être lus. Éléments d’un [Platform::Collections :: Vector](../cppcx/platform-collections-vector-class.md) ou[Platform::Collections :: vectorview](../cppcx/platform-collections-vectorview-class.md) collection est accessible à l’aide d’un itérateur ou de la collection [Vector::GetAt](../cppcx/platform-collections-vector-class.md#getat) et un index. Éléments d’une collection associative sont accessibles à l’aide de la collection [Map::Lookup](../cppcx/platform-collections-map-class.md#lookup) et une clé.

[classe Platform::Collections::Map](../cppcx/platform-collections-map-class.md)<br/>
Collection associative modifiable. Les éléments de mappage sont des paires clé/valeur. La recherche d'une clé pour récupérer sa valeur associée et l'itération sur toutes les paires clé/valeur sont toutes deux prises en charge.

`Map` et `MapView` sont basés sur un modèle de `<K, V, C = std::less<K>>`; vous pouvez donc personnaliser le comparateur.  En outre, `Vector` et `VectorView` sont basés sur des modèles de `<T, E = std::equal_to<T>>` pour vous permettre de personnaliser le comportement de `IndexOf()`. C'est important principalement pour le `Vector` et le `VectorView` des structures de valeur. Par exemple, pour créer un vecteur\<Windows::Foundation :: DateTime >, vous devez fournir un comparateur personnalisé, car DateTime ne surcharge pas l’opérateur ==.

[classe Platform::Collections::MapView](../cppcx/platform-collections-mapview-class.md)<br/>
Version en lecture seule d'un `Map`.

[Platform::Collections::Vector Class](../cppcx/platform-collections-vector-class.md)<br/>
Collection de séquence modifiable. `Vector<T>` prend en charge les opérations d'accès aléatoire en temps constant et les opérations d' [ajout](../cppcx/platform-collections-vector-class.md#append) en temps constant amorti.

[classe Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md)<br/>
Version en lecture seule d'un `Vector`.

[Platform::Collections::InputIterator, classe](../cppcx/platform-collections-inputiterator-class.md)<br/>
Itérateur STL qui satisfait aux spécifications d'un itérateur d'entrée STL.

[Platform::Collections::VectorIterator, classe](../cppcx/platform-collections-vectoriterator-class.md)<br/>
Itérateur STL qui répond aux spécifications d'un itérateur à accès aléatoire mutable STL.

[Platform::Collections::VectorViewIterator, classe](../cppcx/platform-collections-vectorviewiterator-class.md)<br/>
Itérateur STL qui répond aux spécifications d'un itérateur à accès aléatoire  `const` STL.

### <a name="begin-and-end-functions"></a>Fonctions begin() et end()

Pour simplifier l’utilisation de la bibliothèque STL pour traiter les `Vector`, `VectorView`, `Map`, `MapView`et arbitraire `Windows::Foundation::Collections` objets, C++ / c++ / CX prend en charge les surcharges de la [begin, fonction](../cppcx/begin-function.md) et [fin Fonction](../cppcx/end-function.md) des fonctions non-membres.

Le tableau ci-dessous répertorie les itérateurs et fonctions disponibles.

|Iterators|Fonctions|
|---------------|---------------|
|[Platform::Collections::VectorIterator\<T>](../cppcx/platform-collections-vectoriterator-class.md)<br /><br /> (Stocke en interne [Windows::Foundation :: Collections :: IVector\<T >](https://msdn.microsoft.com/library/windows/apps/br206631.aspx) et int.)|[commencer](../cppcx/begin-function.md)/ [fin](../cppcx/end-function.md)([Windows::Foundation :: Collections :: IVector\<T >](https://msdn.microsoft.com/library/windows/apps/br206631.aspx))|
|[Platform::Collections :: vectorviewiterator\<T >](../cppcx/platform-collections-vectorviewiterator-class.md)<br /><br /> (Stocke en interne [IVectorView\<T >](https://msdn.microsoft.com/library/windows/apps/br226058.aspx)^ et int.)|[commencer](../cppcx/begin-function.md)/ [fin](../cppcx/end-function.md) ([IVectorView\<T >](https://msdn.microsoft.com/library/windows/apps/br226058.aspx)^)|
|[Platform::Collections :: inputiterator\<T >](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Stocke en interne [IIterator\<T >](https://msdn.microsoft.com/library/windows/apps/br226026.aspx)^ et T.)|[commencer](../cppcx/begin-function.md)/ [fin](../cppcx/end-function.md) ([IIterable\<T >](https://msdn.microsoft.com/library/windows/apps/br226024.aspx))|
|[Platform::Collections::InputIterator<IKeyValuePair\<K, V>^>](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Stocke en interne [IIterator\<T >](https://msdn.microsoft.com/library/windows/apps/br226026.aspx)^ et T.)|[commencer](../cppcx/begin-function.md)/ [fin](../cppcx/end-function.md) ([IMap\<K, V >](/uwp/api/Windows.Foundation.Collections.IMap_K_V_).|
|[Platform::Collections::InputIterator<IKeyValuePair\<K, V>^>](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Stocke en interne [IIterator\<T >](https://msdn.microsoft.com/library/windows/apps/br226026.aspx)^ et T.)|[commencer](../cppcx/begin-function.md)/ [fin](../cppcx/end-function.md) ([Windows :: Foundation::Collections::IMapView]/uwp/api/Windows.Foundation.Collections.IMapView_K_V_))|

### <a name="collection-change-events"></a>Événements de modification de collection

`Vector` et `Map` prennent en charge la liaison des données dans les collections XAML en implémentant des événements qui se produisent lorsqu'un objet de collection est changé ou réinitialisé, ou lorsque l'élément d'une collection est inséré, supprimé ou modifié. Vous pouvez écrire vos propres types qui prennent en charge la liaison de données, bien que vous ne puissiez pas hériter de `Map` ou de `Vector` car ces types sont verrouillés.

Les délégués [Windows::Foundation::Collections::VectorChangedEventHandler](/uwp/api/windows.foundation.collections.vectorchangedeventhandler) et [Windows::Foundation::Collections::MapChangedEventHandler](/uwp/api/windows.foundation.collections.mapchangedeventhandler) spécifient les signatures des gestionnaires d’événements pour les événements de modification de collection. La classe d’énumération publique [Windows::Foundation::Collections::CollectionChange](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.collectionchange.aspx) , ainsi que les classes ref `Platform::Collection::Details::MapChangedEventArgs` et `Platform::Collections::Details::VectorChangedEventArgs` stockent les arguments d’événement pour déterminer ce qui a déclenché l’événement. Le `*EventArgs` types sont définis dans le `Details` espace de noms, car vous n’êtes pas obligé de construire ni de les consommer explicitement quand vous utilisez `Map` ou `Vector`.

## <a name="see-also"></a>Voir aussi

[Système de type](../cppcx/type-system-c-cx.md)<br/>
[Référence du langage Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Référence des espaces de noms](../cppcx/namespaces-reference-c-cx.md)