---
title: Collections (C++/CX)
ms.date: 11/19/2018
ms.assetid: 914da30b-aac5-4cd7-9da3-a5ac08cdd72c
ms.openlocfilehash: 59e73b803a0878e88361c7fe75cff556b8eeedcd
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032315"
---
# <a name="collections-ccx"></a>Collections (C++/CX)

Dans le cadre d’un programme CMD/CX, vous pouvez utiliser gratuitement les conteneurs Standard Template Library (STL) ou tout autre type de collecte défini par l’utilisateur. Toutefois, lorsque vous passez des collections d’avant en arrière à travers l’interface binaire de l’application Windows Runtime (ABI), par exemple, à un contrôle XAML ou à un client JavaScript, vous devez utiliser les types de collecte Windows Runtime.

Le Windows Runtime définit les interfaces pour les collections et les types connexes, et C /CX fournit les implémentations en béton CMD dans le fichier d’en-tête collection.h. Cette illustration montre les relations entre les types de collection :

![C&#43;&#43;&#47;arbre d’héritage CX pour les types de collecte](../cppcx/media/cppcxcollectionsinheritancetree.png "C&#43;&#43;&#47;arbre d’héritage CX pour les types de collecte")

- La [classe Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) ressemble à la [classe std::vector](../standard-library/vector-class.md).

- La [classe Platform::Collections::Map](../cppcx/platform-collections-map-class.md) ressemble à la [classe std::map](../standard-library/map-class.md).

- La[classe Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md) et la[classe Platform::Collections::MapView](../cppcx/platform-collections-mapview-class.md) sont des versions en lecture seule de `Vector` et la `Map`.

- Les itérateurs sont définis dans [Platform::Collections Namespace](../cppcx/platform-collections-namespace.md). Ces itérateurs répondent aux spécifications des itérateurs STL et permettent d’utiliser [std::find](../standard-library/algorithm-functions.md#find),  [std::count_if](../standard-library/algorithm-functions.md#count_if)et d’autres algorithmes STL sur n’importe quel type d’interface [Windows::Foundation::Collections](/uwp/api/windows.foundation.collections) ou type concret [Platform::Collections](../cppcx/platform-collections-namespace.md) . Par exemple, cela signifie que vous pouvez itérer une collection dans un composant Windows Runtime qui est créé dans C et y appliquer un algorithme STL.

   > [!IMPORTANT]
   > Les itérateurs de proxy `VectorIterator` et `VectorViewIterator` utilisent les objets proxy `VectoryProxy<T>` et `ArrowProxy<T>` pour activer l'utilisation avec des conteneurs STL. Pour plus d'informations, consultez « Éléments VectorProxy » dans la suite de cet article.

- Les types de collecte CMD/CX prennent en charge les mêmes garanties de sécurité de thread que les conteneurs STL supportent.

- [Windows::Foundation::Collections::IObservableVector](/uwp/api/windows.foundation.collections.iobservablevector-1) et [Windows::Foundation::Collections::IObservableMap](/uwp/api/windows.foundation.collections.iobservablemap-2) définissent des événements qui sont déclenchés quand la collection est modifiée de différentes manières. En implémentant ces interfaces,  [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) et [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) prennent en charge la liaison de données avec les collections XAML. Par exemple, si vous avez un vecteur `Vector` qui est lié aux données à un `Grid`, lorsque vous ajoutez un élément à une collection, la modification est répercutée dans la grille de l'interface utilisateur.

## <a name="vector-usage"></a>Utilisation de Vector

Lorsque votre classe doit passer un conteneur de séquences à un autre composant Windows Runtime, utilisez [Windows:::Foundation::Collections:: IVector\<T>](/uwp/api/windows.foundation.collections.ivector-1) comme paramètre ou le type de retour, et [plate-forme::Collections::Vector\<T>](../cppcx/platform-collections-vector-class.md) comme implémentation concrète. Si vous tentez d'utiliser un type `Vector` dans une valeur ou un paramètre de retour, l'erreur de compilateur C3986 est générée. Vous pouvez corriger l'erreur en remplaçant le `Vector` par un `IVector`.

> [!IMPORTANT]
> Si vous passez une séquence dans le cadre de votre propre programme, utilisez `Vector` ou `std::vector` car ils sont plus efficaces que `IVector`. Utilisez `IVector` uniquement lorsque vous passez le conteneur à travers l'ABI.
>
> Le système de type Windows Runtime ne prend pas en charge le concept de tableaux déchiquetés\<et donc vous ne pouvez pas passer une plate-forme IVector<::Array T>> comme une valeur de retour ou un paramètre de méthode. Pour passer un tableau en escalier ou une séquence de séquences à travers l'ABI, utilisez `IVector<IVector<T>^>`.

`Vector<T>` fournit les méthodes requises pour ajouter, supprimer les éléments et y accéder dans la collection, et il est implicitement convertible en `IVector<T>`. Vous pouvez également utiliser les algorithmes STL sur les instances de `Vector<T>`. L'exemple ci-dessous illustre l'utilisation de base. Les fonctions [begin](../cppcx/begin-function.md) et [end](../cppcx/end-function.md) sont issues ici de l'espace `Platform::Collections` au lieu de l'espace `std` .

[!code-cpp[cx_collections#01](../cppcx/codesnippet/CPP/collections/class1.cpp#01)]

Si vous avez le `std::vector` code existant qui utilise et que vous souhaitez le `Vector` réutiliser `std::vector` dans un composant Windows Runtime, il suffit d’utiliser l’un des constructeurs qui prend un ou une paire d’itérateurs pour construire un `Vector` au point où vous passez la collection à travers l’ABI. L'exemple ci-dessous indique comment utiliser le constructeur de déplacement `Vector` pour une initialisation efficace à partir d'un `std::vector`. Une fois l'opération de déplacement terminée, la variable `vec` d'origine n'est plus valide.

[!code-cpp[cx_collections#02](../cppcx/codesnippet/CPP/collections/class1.cpp#02)]

Si vous avez un vecteur de chaînes que vous devez passer à travers l'ABI à un futur point, vous devez décider s'il faut créer des chaînes initialement en tant que types `std::wstring` ou `Platform::String^` . Si vous devez effectuer un important traitement sur les chaînes, utilisez `wstring`. Sinon, créez les chaînes en tant que types `Platform::String^` et évitez ainsi d'avoir à les convertir ultérieurement. Vous devez également décider s'il faut placer ces chaînes dans `std:vector` ou `Platform::Collections::Vector` en interne. De manière générale, utilisez `std::vector` et créez ensuite `Platform::Vector` à partir de ce dernier uniquement lorsque vous passez le conteneur à travers l'ABI.

## <a name="value-types-in-vector"></a>Types de valeur relatifs au vecteur

Tout élément à stocker dans [Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md) doit prendre en charge la comparaison d'égalité, implicitement ou à l'aide d'un comparateur [std::equal_to](../standard-library/equal-to-struct.md) personnalisé que vous fournissez. Tous les types de références et tous les types scalaires prennent en charge implicitement les comparaisons d'égalité. Pour les types de valeurs non scalaires tels que [Windows::Foundation::DateTime](/uwp/api/windows.foundation.datetime), ou pour les comparaisons personnalisées, par exemple, `objA->UniqueID == objB->UniqueID`, vous devez fournir un objet de fonction personnalisé.

## <a name="vectorproxy-elements"></a>Éléments VectorProxy

[Plateforme::Collections::VectorIterator](../cppcx/platform-collections-vectoriterator-class.md) and [Platform::Collections::VectorViewIterator](../cppcx/platform-collections-vectorviewiterator-class.md) enable `range for` the use of loops and algorithms like [std::sort](../standard-library/algorithm-functions.md#sort) with an [IVector\<T>](/uwp/api/windows.foundation.collections.ivector-1) container. Toutefois, les éléments `IVector` ne sont pas accessibles par l’intermédiaire du déréférencement de pointeur C++. Ils sont accessibles uniquement avec les méthodes [GetAt](/uwp/api/windows.foundation.collections.ivector-1.getat) et [SetAt](/uwp/api/windows.foundation.collections.ivector-1.setat) . Par conséquent, ces itérateurs `Platform::Details::VectorProxy<T>` `Platform::Details::ArrowProxy<T>` utilisent les classes de __\*__ procuration __->__ et de fournir l’accès aux éléments individuels par , , et __ \[]__ les opérateurs, comme l’exige la Bibliothèque standard. À proprement parler, avec un `IVector<Person^> vec`, le type de `*begin(vec)` est `VectorProxy<Person^>`. Toutefois, l'objet proxy est presque toujours transparent pour votre code. Ces objets proxy ne sont pas documentés car ils servent uniquement à un usage interne par les itérateurs, mais il est utile de savoir comment le mécanisme fonctionne.

Lorsque vous utilisez une boucle `range for` sur les conteneurs `IVector` , utilisez `auto&&` pour permettre à la variable d'itérateur d'effectuer une liaison correcte avec les éléments `VectorProxy` . Si vous utilisez `auto` ou `auto&`, l'avertissement de compilateur C4239 est déclenché et `VectoryProxy` est mentionné dans le texte d'avertissement.

L'illustration suivante montre une boucle `range for` sur un `IVector<Person^>`. Notez que l'exécution est interrompue sur le point d'arrêt à la ligne 64. La fenêtre **Espion express** indique que la variable d'itérateur `p` est en fait un `VectorProxy<Person^>` qui a les variables membres `m_v` et `m_i` . Toutefois, lorsque vous appelez la méthode `GetType` sur cette variable, elle retourne le type identique à l'instance `Person``p2`. Le principal avantage est que, bien que `VectorProxy` et `ArrowProxy` puissent apparaître dans **Espion express**, le débogueur de certaines erreurs de compilateur, il n'est pas nécessaire en général de coder explicitement pour eux.

![VectorProxy à portée&#45;basé pour la boucle](../cppcx/media/vectorproxy-1.png "VectorProxy à portée&#45;basé pour la boucle")

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

Cet exemple montre comment insérer des éléments et les consulter dans [Platform::Collections::Map](../cppcx/platform-collections-map-class.md), puis retourner `Map` sous forme d’un type [Windows::Foundation::Collections::IMapView](/uwp/api/windows.foundation.collections.imapview-2) en lecture seule.

[!code-cpp[cx_collections#04](../cppcx/codesnippet/CPP/collections/class1.cpp#04)]

En général, pour les fonctionnalités de carte intégrées, préférez le type `std::map` pour des raisons de performance. Si vous devez passer le conteneur à travers l’ABI, construisez un [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) à partir de [std::map](../standard-library/map-class.md) et retournez le `Map` sous forme de [Windows::Foundation::Collections::IMap](/uwp/api/windows.foundation.collections.imap-2). Si vous tentez d'utiliser un type `Map` dans une valeur ou un paramètre de retour, l'erreur de compilateur C3986 est générée. Vous pouvez corriger l'erreur en remplaçant le `Map` par un `IMap`. Dans certains cas, par exemple si vous n'effectuez pas un grand nombre de recherches ou d'insertions et que vous passez fréquemment la collection à travers l'ABI, il peut être moins coûteux d'utiliser `Platform::Collections::Map` et d'éviter ainsi le coût de conversion de `std::map`. Dans tous les cas, évitez les recherches et insertions sur un `IMap` , car c'est le moins performant des trois types. Effectuez une conversion en `IMap` uniquement au point où vous passez le conteneur à travers l'ABI.

## <a name="value-types-in-map"></a>Types de valeur relatifs au mappage

Les éléments contenus dans [Platform::Collections::Map](../cppcx/platform-collections-map-class.md) sont classés. Tout élément à stocker dans `Map` doit prendre en charge la comparaison « inférieur à » avec le classement faible strict, implicitement ou à l'aide d'un comparateur personnalisé [stl::less](../standard-library/less-struct.md) que vous fournissez. Les types scalaires prennent en charge la comparaison implicitement. Pour les types de valeurs non scalaires tels que `Windows::Foundation::DateTime`, ou pour les comparaisons personnalisées, par exemple, `objA->UniqueID < objB->UniqueID`, vous devez fournir un comparateur personnalisé.

## <a name="collection-types"></a>Types de collections

Les collections sont classées en quatre catégories : versions modifiables et versions en lecture seule des collections séquentielles et associatives. De plus, le CMD/CX améliore les collections en offrant trois classes d’itérateurs qui simplifient l’accès aux collections.

Les éléments d'une collection modifiable peuvent être modifiés, mais les éléments d'une collection en lecture seule, appelée *vue*, peuvent uniquement être lus. Éléments d’une [plate-forme::Collections::Vector](../cppcx/platform-collections-vector-class.md) or[Platform::Collections::VectorView](../cppcx/platform-collections-vectorview-class.md) collection peut être consulté en utilisant un itérateur ou le vector de la [collection::GetAt](../cppcx/platform-collections-vector-class.md#getat) et un index. Des éléments d’une collection associative peuvent être consultés en utilisant la carte de la collection [: : Lookup](../cppcx/platform-collections-map-class.md#lookup) et une clé.

[classe Platform::Collections::Map](../cppcx/platform-collections-map-class.md)<br/>
Collection associative modifiable. Les éléments de mappage sont des paires clé/valeur. La recherche d'une clé pour récupérer sa valeur associée et l'itération sur toutes les paires clé/valeur sont toutes deux prises en charge.

`Map` et `MapView` sont basés sur un modèle de `<K, V, C = std::less<K>>`; vous pouvez donc personnaliser le comparateur.  En outre, `Vector` et `VectorView` sont basés sur des modèles de `<T, E = std::equal_to<T>>` pour vous permettre de personnaliser le comportement de `IndexOf()`. C'est important principalement pour le `Vector` et le `VectorView` des structures de valeur. Par exemple, pour\<créer un Vector Windows::Foundation::DateTime>, vous devez fournir un comparateur personnalisé parce que DateTime ne surcharge pas l’opérateur.

[Platform::Collections::MapView, classe](../cppcx/platform-collections-mapview-class.md)<br/>
Version en lecture seule d'un `Map`.

[Platform::Collections::Vector, classe](../cppcx/platform-collections-vector-class.md)<br/>
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

Pour simplifier l’utilisation du `Vector`TSL pour `VectorView`traiter, , , `Map` `MapView`, et les objets arbitraires, `Windows::Foundation::Collections` C '/CX prend en charge les surcharges de la fonction de [départ](../cppcx/begin-function.md) et de fonction de [fin](../cppcx/end-function.md) fonction fonction fonction non-membre fonctions.

Le tableau ci-dessous répertorie les itérateurs et fonctions disponibles.

|Iterators|Fonctions|
|---------------|---------------|
|[Plateforme::Collections::VectorIterator\<T>](../cppcx/platform-collections-vectoriterator-class.md)<br /><br /> (Magasins internes [Windows::Foundation::Collections::\<IVector T>](/uwp/api/windows.foundation.collections.ivector-1) and int.)|[début](../cppcx/begin-function.md)/ [de fin](../cppcx/end-function.md)([Windows::Foundation:Collections:: IVector\<T>](/uwp/api/windows.foundation.collections.ivector-1))|
|[Plateforme::Collections::VectorViewIterator\<T>](../cppcx/platform-collections-vectorviewiterator-class.md)<br /><br /> (Magasins internes [IVectorView\<T>](/uwp/api/windows.foundation.collections.ivectorview-1)et int.)|[début de](../cppcx/begin-function.md)/ [l’extrémité](../cppcx/end-function.md) [(IVectorView\<T>) ](/uwp/api/windows.foundation.collections.ivectorview-1)|
|[Plateforme::Collections::InputIterator\<T>](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Magasins internes [IIterator\<T>](/uwp/api/windows.foundation.collections.iiterator-1)et T.)|[début de](../cppcx/begin-function.md)/ [fin](../cppcx/end-function.md) ([\<IIterable T>](/uwp/api/windows.foundation.collections.iiterable-1))|
|[Plateforme::Collections::InputIterator<IKeyValuePair\<K, V>>](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Magasins internes [IIterator\<T>](/uwp/api/windows.foundation.collections.iiterator-1)et T.)|[début de](../cppcx/begin-function.md)/ [la fin](../cppcx/end-function.md) ([IMap\<K,V>](/uwp/api/windows.foundation.collections.imap-2).|
|[Plateforme::Collections::InputIterator<IKeyValuePair\<K, V>>](../cppcx/platform-collections-inputiterator-class.md)<br /><br /> (Magasins internes [IIterator\<T>](/uwp/api/windows.foundation.collections.iiterator-1)et T.)|[début de](../cppcx/begin-function.md)/ [fin](../cppcx/end-function.md) ([Windows::Foundation:Collections::IMapView](/uwp/api/windows.foundation.collections.imapview-2))|

### <a name="collection-change-events"></a>Événements de modification de collection

`Vector` et `Map` prennent en charge la liaison des données dans les collections XAML en implémentant des événements qui se produisent lorsqu'un objet de collection est changé ou réinitialisé, ou lorsque l'élément d'une collection est inséré, supprimé ou modifié. Vous pouvez écrire vos propres types qui prennent en charge la liaison de données, bien que vous ne puissiez pas hériter de `Map` ou de `Vector` car ces types sont verrouillés.

Les délégués [Windows::Foundation::Collections::VectorChangedEventHandler](/uwp/api/windows.foundation.collections.vectorchangedeventhandler-1) et [Windows::Foundation::Collections::MapChangedEventHandler](/uwp/api/windows.foundation.collections.mapchangedeventhandler-2) spécifient les signatures des gestionnaires d’événements pour les événements de modification de collection. La classe d’énumération publique [Windows::Foundation::Collections::CollectionChange](/uwp/api/windows.foundation.collections.collectionchange) , ainsi que les classes ref `Platform::Collection::Details::MapChangedEventArgs` et `Platform::Collections::Details::VectorChangedEventArgs` stockent les arguments d’événement pour déterminer ce qui a déclenché l’événement. Les `*EventArgs` types sont `Details` définis dans l’espace nom parce que vous `Map` n’avez pas à les construire ou à les consommer explicitement lorsque vous utilisez ou `Vector`.

## <a name="see-also"></a>Voir aussi

[Système de types](../cppcx/type-system-c-cx.md)<br/>
[Référence linguistique CMD/CX](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Référence aux espaces de noms](../cppcx/namespaces-reference-c-cx.md)
