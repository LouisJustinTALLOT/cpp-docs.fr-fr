---
title: À l’aide de C++ AMP dans les applications UWP | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 85577298-2c28-4209-9470-eb21048615db
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5736c84f21535222de5659780968efd98e1467da
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33696148"
---
# <a name="using-c-amp-in-uwp-apps"></a>À l’aide de C++ AMP dans les applications UWP
Vous pouvez utiliser C++ AMP (C++ Accelerated Massive Parallelism) dans votre application de plateforme Windows universelle (UWP) pour effectuer des calculs sur le processeur graphique (GPU) ou d’autres accélérateurs de calculs. Toutefois, C++ AMP ne fournissent des API pour travailler directement avec les types Windows Runtime, et le Windows Runtime ne fournit pas un wrapper pour C++ AMP. Lorsque vous utilisez des types Windows Runtime dans votre code, y compris celles que vous avez créé vous-même, vous devez convertir les types qui sont compatibles avec C++ AMP.  
  
## <a name="performance-considerations"></a>Considérations sur les performances  
 Si vous utilisez [!INCLUDE[cppwrt](../../build/reference/includes/cppwrt_md.md)] ([!INCLUDE[cppwrt_short](../../build/reference/includes/cppwrt_short_md.md)]) pour créer votre application de plateforme Windows universelle (UWP), nous vous recommandons d’utiliser des types de données (POD) brut basés ancien avec stockage contigu, par exemple, `std::vector` ou tableaux de style C, pour les données qui seront utilisées avec C++ AMP. Cela peut vous aider à obtenir de meilleures performances qu’à l’aide des types non POD ou les conteneurs Windows RT, car aucun marshaling n’est nécessaire.  
  
 Dans un noyau de C++ AMP, pour accéder aux données qui est stocké de cette façon, encapsulez simplement la `std::vector` ou tableau de stockage dans un `concurrency::array_view` , puis utilisez l’affichage de tableau dans un `concurrency::parallel_for_each` boucle :  
  
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
 Lorsque vous travaillez avec APIs Windows Runtime, vous pouvez souhaiter utiliser C++ AMP sur les données stockées dans un conteneur Windows Runtime une `Platform::Array<T>^` ou dans les types de données complexes telles que les classes ou les structures déclarées à l’aide de la `ref` mot clé ou le `value`</C4>(motclé). Dans ces situations, vous devrez effectuer du travail supplémentaire pour mettre les données à la disposition de C++ AMP.  
  
### <a name="platformarrayt-where-t-is-a-pod-type"></a>Platform::Array\<T > ^, où T est un type POD  
 Lorsque vous rencontrez un `Platform::Array<T>^` et T est un type POD, vous pouvez accéder à son emplacement de stockage sous-jacent en utilisant simplement la `get` fonction membre :  
  
```cpp  
Platform::Array<float>^ arr; // Assume that this was returned by a Windows Runtime API  
concurrency::array_view<float, 1> av(arr->Length, &arr->get(0));
```  
  
 Si T n’est pas un type POD, vous pouvez utiliser la technique décrite dans la section suivante pour utiliser les données avec C++ AMP.  
  
### <a name="windows-runtime-types-ref-classes-and-value-classes"></a>Types Windows Runtime : classes de référence et classes de valeur  
 C++ AMP ne prend pas en charge les types de données complexes. Cela inclut les types non POD et tous les types qui sont déclarés à l’aide de la `ref` mot clé ou le `value` (mot clé). Si un type non pris en charge est utilisé dans un `restrict(amp)` contexte, une erreur de compilation est générée.  
  
 Lorsque vous rencontrez un type non pris en charge, vous pouvez copier des éléments de ses données dans un `concurrency::array` objet. En plus de rendre les données disponibles pour C++ AMP consommer, cette approche de la copie manuelle peut également améliorer les performances en optimisant la localité des données et en vous assurant que les données ne seront pas utilisées n’est pas copiées dans l’accélérateur. Vous pouvez améliorer les performances davantage à l’aide un *intermédiaire tableau*, qui est une forme particulière de `concurrency::array` qui fournit un indicateur à l’exécution de l’AMP que le tableau doit être optimisé pour le transfert de fréquent entre elle et d’autres tableaux sur la accélérateur spécifié.  
  
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
 [Créer votre première application de plateforme Windows universelle à l’aide de C++](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)   
 [Création de composants Windows Runtime en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)

