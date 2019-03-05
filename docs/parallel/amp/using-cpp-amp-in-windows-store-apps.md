---
title: À l’aide de C++ AMP dans les applications UWP
ms.date: 11/04/2016
ms.assetid: 85577298-2c28-4209-9470-eb21048615db
ms.openlocfilehash: 31fede0a2419e56d53cb16521b08067dac5facc6
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272657"
---
# <a name="using-c-amp-in-uwp-apps"></a>À l’aide de C++ AMP dans les applications UWP

Vous pouvez utiliser C++ AMP (C++ Accelerated Massive Parallelism) dans votre application de plateforme universelle Windows (UWP) pour effectuer des calculs sur le GPU (Graphics Processing Unit) ou d’autres accélérateurs de calcul. Toutefois, C++ AMP ne fournissent des API pour travailler directement avec les types Windows Runtime, et le Runtime Windows ne fournit pas un wrapper pour C++ AMP. Lorsque vous utilisez des types Windows Runtime dans votre code, y compris celles que vous avez créée vous-même, vous devez convertir les types qui sont compatibles avec C++ AMP.

## <a name="performance-considerations"></a>Considérations sur les performances

Si vous utilisez des extensions du composant C++ de Visual C++ / c++ / CX pour créer votre application Universal Windows Platform (UWP), nous vous recommandons d’utiliser des types de plain-old-data (POD) avec le stockage contigu, par exemple, `std::vector` ou tableaux de style C, pour les données qui seront utilisé avec C++ AMP. Cela peut vous aider à atteindre de meilleures performances qu’à l’aide de types non POD ou les conteneurs Windows RT, car aucun marshaling ne doit se produire.

Dans un noyau C++ AMP, pour accéder aux données qui est stocké de cette façon, il suffit d’encapsuler le `std::vector` ou stockage de groupe dans un `concurrency::array_view` , puis utilisez l’affichage de tableau dans un `concurrency::parallel_for_each` boucle :

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

Lorsque vous travaillez avec Windows Runtime APIs, vous pouvez souhaiter utiliser C++ AMP sur les données stockées dans un conteneur Windows Runtime comme un `Platform::Array<T>^` ou dans les types de données complexes telles que les classes ou structs qui sont déclarés à l’aide de la **ref** mot clé ou le **valeur** mot clé. Dans ces situations, vous devez effectuer un travail supplémentaire pour rendre les données C++ AMP.

### <a name="platformarrayt-where-t-is-a-pod-type"></a>Platform::Array\<T > ^, où T est un type POD

Lorsque vous rencontrez un `Platform::Array<T>^` et T est un type POD, vous pouvez accéder à son stockage sous-jacent en utilisant simplement le `get` fonction membre :

```cpp
Platform::Array<float>^ arr; // Assume that this was returned by a Windows Runtime API
concurrency::array_view<float, 1> av(arr->Length, &arr->get(0));
```

Si T n’est pas un type POD, vous pouvez utiliser la technique décrite dans la section suivante pour utiliser les données avec C++ AMP.

### <a name="windows-runtime-types-ref-classes-and-value-classes"></a>Types Windows Runtime : classes de référence et classes de valeur

C++ AMP ne prend pas en charge les types de données complexes. Cela inclut les types non POD et tous les types qui sont déclarés à l’aide de la **ref** mot clé ou le **valeur** mot clé. Si un type non pris en charge est utilisé dans un `restrict(amp)` contexte, une erreur de compilation est générée.

Lorsque vous rencontrez un type non pris en charge, vous pouvez copier les parties intéressantes de ses données dans un `concurrency::array` objet. En plus de rendre les données disponibles pour C++ AMP à consommer, cette approche de la copie manuelle peut également améliorer les performances en optimisant la localité des données et en garantissant que les données ne seront pas utilisées ne seront pas copiées à l’accélérateur. Vous pouvez améliorer davantage les performances en utilisant un *tableau intermédiaire*, qui est une forme spéciale de `concurrency::array` qui fournit une indication au runtime AMP le tableau doit être optimisé pour un transfert fréquent entre elles et d’autres tableaux sur la accélérateur spécifié.

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
