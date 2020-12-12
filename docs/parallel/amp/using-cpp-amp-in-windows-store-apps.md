---
description: 'En savoir plus sur : utilisation de C++ AMP dans des applications UWP'
title: Utilisation de C++ AMP dans des applications UWP
ms.date: 11/04/2016
ms.assetid: 85577298-2c28-4209-9470-eb21048615db
ms.openlocfilehash: 91c7b147ff89a1fe19ebe1b18e465533053542d0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97314475"
---
# <a name="using-c-amp-in-uwp-apps"></a>Utilisation de C++ AMP dans des applications UWP

Vous pouvez utiliser C++ AMP (C++ Accelerated Massive Parallelism) dans votre application plateforme Windows universelle (UWP) pour effectuer des calculs sur le GPU (unité de traitement graphique) ou d’autres accélérateurs de calcul. Toutefois, C++ AMP ne fournit pas d’API pour travailler directement avec les types de Windows Runtime, et le Windows Runtime ne fournit pas de wrapper pour C++ AMP. Quand vous utilisez des types de Windows Runtime dans votre code, y compris ceux que vous avez créés vous-même, vous devez les convertir en types compatibles avec C++ AMP.

## <a name="performance-considerations"></a>Considérations relatives aux performances

Si vous utilisez Visual C++ extensions de composant C++/CX pour créer votre application plateforme Windows universelle (UWP), nous vous recommandons d’utiliser des types POD (Plain-Old-Data) avec un stockage contigu, par exemple `std::vector` ou des tableaux de style C, pour les données qui seront utilisées avec C++ amp. Cela peut vous aider à obtenir des performances supérieures à celles des types non POD ou des conteneurs Windows RT, car aucun marshaling ne doit se produire.

Dans un noyau C++ AMP, pour accéder aux données stockées de cette façon, encapsulez simplement le `std::vector` stockage de tableau ou dans un, puis `concurrency::array_view` Utilisez la vue de tableau dans une `concurrency::parallel_for_each` boucle :

```cpp
// simple vector addition example
std::vector<int> data0(1024, 1);
std::vector<int> data1(1024, 2);
std::vector<int> data_out(data0.size(), 0);

concurrency::array_view<int, 1> av0(data0.size(), data0);
concurrency::array_view<int, 1> av1(data1.size(), data1);
concurrency::array_view<int, 1> av2(data_out.size(), data2);

av2.discard_data();

concurrency::parallel_for_each(av0.extent, [=](concurrency::index<1> idx) restrict(amp)
    {
        av2[idx] = av0[idx] + av1[idx];
    });
```

## <a name="marshaling-windows-runtime-types"></a>Marshaling des types Windows Runtime

Quand vous travaillez avec des API Windows Runtime, vous pouvez utiliser des C++ AMP sur les données stockées dans un conteneur Windows Runtime tel que `Platform::Array<T>^` ou dans des types de données complexes tels que des classes ou des structs déclarés à l’aide du mot clé **ref** ou du mot clé **value** . Dans ces situations, vous devez effectuer des tâches supplémentaires pour que les données soient disponibles pour C++ AMP.

### <a name="platformarrayt-where-t-is-a-pod-type"></a>Platform :: array \<T> ^, où T est un type Pod

Lorsque vous rencontrez un `Platform::Array<T>^` et que T est un type Pod, vous pouvez accéder à son stockage sous-jacent simplement à l’aide de la `get` fonction membre :

```cpp
Platform::Array<float>^ arr; // Assume that this was returned by a Windows Runtime API
concurrency::array_view<float, 1> av(arr->Length, &arr->get(0));
```

Si T n’est pas un type POD, utilisez la technique décrite dans la section suivante pour utiliser les données avec C++ AMP.

### <a name="windows-runtime-types-ref-classes-and-value-classes"></a>Types Windows Runtime : classes de référence et classes de valeur

C++ AMP ne prend pas en charge les types de données complexes. Cela comprend les types non POD et tous les types déclarés à l’aide du mot clé **ref** ou du mot clé **value** . Si un type non pris en charge est utilisé dans un `restrict(amp)` contexte, une erreur de compilation est générée.

Lorsque vous rencontrez un type non pris en charge, vous pouvez copier des parties intéressantes de ses données dans un `concurrency::array` objet. En plus de rendre les données disponibles pour une utilisation C++ AMP, cette approche de copie manuelle peut également améliorer les performances en optimisant la localité des données et en garantissant que les données qui ne seront pas utilisées ne sont pas copiées dans l’accélérateur. Vous pouvez améliorer davantage les performances à l’aide d’un *tableau de mise en lots*, qui est une forme spéciale de `concurrency::array` qui fournit une indication au runtime amp que le tableau doit être optimisé pour un transfert fréquent entre celui-ci et d’autres tableaux sur l’accélérateur spécifié.

```cpp
// pixel_color.h
ref class pixel_color sealed
{
public:
    pixel_color(Platform::String^ color_name, int red, int green, int blue)
    {
        name = color_name;
        r = red;
        g = green;
        b = blue;
    }

    property Platform::String^ name;
    property int r;
    property int g;
    property int b;
};

// Some other file

std::vector<pixel_color^> pixels (256);

for (pixel_color ^pixel : pixels)
{
    pixels.push_back(ref new pixel_color("blue", 0, 0, 255));
}

// Create the accelerators
auto cpuAccelerator = concurrency::accelerator(concurrency::accelerator::cpu_accelerator);
auto devAccelerator = concurrency::accelerator(concurrency::accelerator::default_accelerator);

// Create the staging arrays
concurrency::array<float, 1> red_vec(256, cpuAccelerator.default_view, devAccelerator.default_view);
concurrency::array<float, 1>  blue_vec(256, cpuAccelerator.default_view, devAccelerator.default_view);

// Extract data from the complex array of structs into staging arrays.
concurrency::parallel_for(0, 256, [&](int i)
    {
        red_vec[i] = pixels[i]->r;
        blue_vec[i] = pixels[i]->b;
    });

// Array views are still used to copy data to the accelerator
concurrency::array_view<float, 1> av_red(red_vec);
concurrency::array_view<float, 1> av_blue(blue_vec);

// Change all pixels from blue to red.
concurrency::parallel_for_each(av_red.extent, [=](index<1> idx) restrict(amp)
    {
        av_red[idx] = 255;
        av_blue[idx] = 0;
    });
```

## <a name="see-also"></a>Voir aussi

[Créer votre première application UWP à l’aide de C++](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)<br/>
[Création de composants Windows Runtime en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
