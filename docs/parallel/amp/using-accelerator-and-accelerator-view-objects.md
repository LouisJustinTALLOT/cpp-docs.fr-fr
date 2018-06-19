---
title: À l’aide des objets accelerator et accelerator_view | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 18f0dc66-8236-4420-9f46-1a14f2c3fba1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9e0f86467de8256eaecbfbf42765de551a1e2f6e
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690609"
---
# <a name="using-accelerator-and-acceleratorview-objects"></a>Utilisation des objets accelerator et accelerator_view
Vous pouvez utiliser la [accelerator](../../parallel/amp/reference/accelerator-class.md) et [accelerator_view](../../parallel/amp/reference/accelerator-view-class.md) des classes pour spécifier le périphérique ou l’émulateur pour exécuter votre code C++ AMP sur. Un système peut avoir plusieurs périphériques ou les émulateurs qui varient selon la quantité de mémoire, la prise en charge de la mémoire partagée, support de débogage ou prise en charge de la double précision. C++ Accelerated les Massive Parallelism (C++ AMP) fournit des API que vous pouvez utiliser pour examiner les accélérateurs disponibles, définissez un en tant que la valeur par défaut, indiquez plusieurs accelerator_views différents pour les appels multiples à parallel_for_each et effectuer des tâches de débogage spéciales.  
  
## <a name="using-the-default-accelerator"></a>À l’aide de l’accélérateur par défaut  
 Le runtime C++ AMP choisit un accélérateur par défaut, sauf si vous écrivez du code permettant de sélectionner une valeur spécifique. Le runtime sélectionne l’accélérateur par défaut comme suit :  
  
1.  Si l’application s’exécute en mode débogage, un accélérateur qui prend en charge le débogage.  
  
2.  Dans le cas contraire, l’accélérateur qui est spécifié par la variable d’environnement CPPAMP_DEFAULT_ACCELERATOR, s’il est défini.  
  
3.  Sinon, un périphérique non émulé.  
  
4.  Dans le cas contraire, le périphérique ayant la plus grande quantité de mémoire disponible.  
  
5.  Sinon, un périphérique qui n’est pas attaché à l’affichage.  
  
 En outre, le runtime spécifie un `access_type` de `access_type_auto` pour l’accélérateur par défaut. Cela signifie que l’accélérateur par défaut utilise la mémoire partagée si elle est prise en charge et si ses caractéristiques de performances (la bande passante et la latence) sont connus pour être identique à une mémoire dédiée (non partagés).  
  
 Vous pouvez déterminer les propriétés de l’accélérateur par défaut en créant l’accélérateur par défaut et en examinant ses propriétés. L’exemple de code suivant imprime le chemin d’accès, la quantité de mémoire de l’accélérateur, prise en charge de la mémoire partagée, prise en charge de la double précision et la prise en charge de double précision limitée de l’accélérateur par défaut.  
  
```cpp  
void default_properties() {  
    accelerator default_acc;  
    std::wcout << default_acc.device_path << "\n";  
    std::wcout << default_acc.dedicated_memory << "\n";  
    std::wcout << (accs[i].supports_cpu_shared_memory ?   
        "CPU shared memory: true" : "CPU shared memory: false") << "\n";  
    std::wcout << (accs[i].supports_double_precision ?   
        "double precision: true" : "double precision: false") << "\n";  
    std::wcout << (accs[i].supports_limited_double_precision ?   
        "limited double precision: true" : "limited double precision: false") << "\n";  
}  
 
```  
  
### <a name="cppampdefaultaccelerator-environment-variable"></a>Variable d’environnement CPPAMP_DEFAULT_ACCELERATOR  
 Vous pouvez définir la variable d’environnement CPPAMP_DEFAULT_ACCELERATOR pour spécifier le `accelerator::device_path` de l’accélérateur par défaut. Le chemin d’accès dépend du matériel. Le code suivant utilise le `accelerator::get_all` de fonction pour récupérer la liste des accélérateurs de disponible, puis affiche le chemin d’accès et les caractéristiques de chaque accélérateur.  
  
```cpp  
void list_all_accelerators()  
{  
    std::vector<accelerator> accs = accelerator::get_all();  
  
    for (int i = 0; i <accs.size(); i++) {  
        std::wcout << accs[i].device_path << "\n";  
        std::wcout << accs[i].dedicated_memory << "\n";  
        std::wcout << (accs[i].supports_cpu_shared_memory ?   
            "CPU shared memory: true" : "CPU shared memory: false") << "\n";  
        std::wcout << (accs[i].supports_double_precision ?   
            "double precision: true" : "double precision: false") << "\n";  
        std::wcout << (accs[i].supports_limited_double_precision ?   
            "limited double precision: true" : "limited double precision: false") << "\n";  
    }  
}  
```  
  
## <a name="selecting-an-accelerator"></a>Sélection d’un accélérateur  
 Pour sélectionner un accélérateur, utilisez la `accelerator::get_all` méthode pour récupérer la liste des accélérateurs de disponibles, puis sélectionnez une basée sur ses propriétés. Cet exemple montre comment choisir l’accélérateur qui a le plus de mémoire :  
  
```cpp  
void pick_with_most_memory()  
{  
    std::vector<accelerator> accs = accelerator::get_all();
    accelerator acc_chosen = accs[0];  
    
    for (int i = 0; i <accs.size(); i++) {  
        if (accs[i].dedicated_memory> acc_chosen.dedicated_memory) {  
            acc_chosen = accs[i];  
        }  
    }  
 
    std::wcout << "The accelerator with the most memory is "    
        << acc_chosen.device_path << "\n"  
        << acc_chosen.dedicated_memory << ".\n";  
}  
```  
  
> [!NOTE]
>  Parmi les accélérateurs sont retournés par `accelerator::get_all` est l’accélérateur de l’UC. Vous ne pouvez pas exécuter du code sur l’accélérateur de l’UC. Pour exclure l’accélérateur de l’UC, comparez la valeur de la [chemin_unité](reference/accelerator-class.md#device_path) propriété de l’accélérateur qui est retourné par `accelerator::get_all` avec la valeur de la [accelerator::cpu_accelerator](reference/accelerator-class.md#cpu_accelerator). Pour plus d’informations, consultez la section « Accélérateurs spécial » dans cet article.  
  
## <a name="shared-memory"></a>Mémoire partagée  
 Mémoire partagée est la mémoire qui sont accessibles par le processeur et de l’accélérateur. L’utilisation de mémoire partagée élimine ou réduit sensiblement la surcharge de copie des données entre le processeur et de l’accélérateur. Bien que la mémoire est partagée, il ne peut pas être accessibles simultanément par le processeur et de l’accélérateur, et cela entraîne un comportement non défini. La propriété d’un accélérateur [supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory) retourne `true` si l’accélérateur prend en charge la mémoire partagée et le [default_cpu_access_type](reference/accelerator-class.md#default_cpu_access_type) propriété obtient la valeur par défaut [access_type](reference/concurrency-namespace-enums-amp.md#access_type) pour la mémoire allouée sur le `accelerator`— par exemple, `array`associées à la `accelerator`, ou `array_view` objets accédés sur le `accelerator`. 
  
 Le runtime C++ AMP choisit automatiquement la meilleure option par défaut `access_type` pour chaque `accelerator`, mais les caractéristiques de performances (la bande passante et la latence) de mémoire partagée peuvent être inférieures à celles de la mémoire de dédié accélérateur (non partagés) lors de la lecture à partir de l’UC, l’écriture à partir de l’UC, ou les deux. Si la mémoire partagée effectue ainsi que de la mémoire dédiée pour la lecture et l’écriture de l’unité centrale, le runtime par défaut est `access_type_read_write`; sinon, le runtime sélectionne une valeur par défaut plus conservateur pour `access_type`et autorise l’application à remplacer si accéder à la mémoire modèles de noyaux de son calcul bénéficient d’une autre `access_type`.  
  
 L’exemple de code suivant montre comment déterminer si l’accélérateur par défaut prend en charge de la mémoire partagée, puis remplace le type d’accès par défaut et crée un `accelerator_view` à partir de celui-ci.  
  
```cpp  
#include <amp.h>  
#include <iostream>  
  
using namespace Concurrency;  
  
int main()  
{  
    accelerator acc = accelerator(accelerator::default_accelerator);  
  
    // Early out if the default accelerator doesn’t support shared memory.  
    if (!acc.supports_cpu_shared_memory)  
    {  
        std::cout << "The default accelerator does not support shared memory" << std::endl;  
        return 1;  
    }  
  
    // Override the default CPU access type.  
    acc.set_default_cpu_access_type(access_type_read_write);  
  
    // Create an accelerator_view from the default accelerator. The  
    // accelerator_view reflects the default_cpu_access_type of the  
    // accelerator it’s associated with.  
    accelerator_view acc_v = acc.default_view;  
}  
```  
  
 Un `accelerator_view` reflète toujours le `default_cpu_access_type` de la `accelerator` lui est associée, et il ne fournit aucune interface pour les remplacer ou modifier ses `access_type`.  
  
## <a name="changing-the-default-accelerator"></a>Modification de l’accélérateur par défaut  
 Vous pouvez modifier l’accélérateur par défaut en appelant le `accelerator::set_default` (méthode). Vous pouvez modifier l’accélérateur par défaut qu’une seule fois par application l’exécution et que vous devez le modifier avant n’importe quel code est exécuté sur le GPU. Retournent de tous les appels de fonction suivants pour modifier l’accélérateur `false`. Si vous souhaitez utiliser un accélérateur différents dans un appel à `parallel_for_each`, lisez la section « Utilisation des accélérateurs plusieurs » dans cet article. L’exemple de code suivant définit l’accélérateur par défaut par un autre qui n’est pas émulée, n’est pas connecté à un affichage et prend en charge double précision.  
  
```cpp  
bool pick_accelerator()  
{  
    std::vector<accelerator> accs = accelerator::get_all();
    accelerator chosen_one;  
 
    auto result = std::find_if(accs.begin(), accs.end(), 
        [] (const accelerator& acc) {  
            return !acc.is_emulated && 
                acc.supports_double_precision && 
                !acc.has_display;  
        });
  
    if (result != accs.end()) {  
        chosen_one = *(result);
    }
  
    std::wcout <<chosen_one.description <<std::endl;  
    bool success = accelerator::set_default(chosen_one.device_path);
    return success;  
}  
```  
  
## <a name="using-multiple-accelerators"></a>À l’aide de plusieurs accélérateurs  
 Il existe deux façons d’utiliser plusieurs accélérateurs de votre application :  

-   Vous pouvez passer `accelerator_view` objets pour les appels à la [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) (méthode).  
  
-   Vous pouvez construire une `array` spécifique à l’aide de l’objet `accelerator_view` objet. Le runtime C + AMP prennent en charge la `accelerator_view` objet capturées `array` objet dans l’expression lambda.  
  
## <a name="special-accelerators"></a>Accélérateurs spéciaux  
 Les chemins d’accès de périphérique des trois accélérateurs spéciaux sont disponibles en tant que propriétés de la `accelerator` classe :  
  
- [Accelerator::direct3d_ref, données membres](reference/accelerator-class.md#direct3d_ref): cet accélérateur monothread utilise des logiciels sur l’UC pour émuler une carte graphique générique. Il est utilisé par défaut pour le débogage, mais il n’est pas utile en production, car il est plus lent que les accélérateurs de matériel. En outre, il est disponible uniquement dans le SDK DirectX et le Kit de développement, et il est peu susceptible d’être installé sur les ordinateurs de vos clients. Pour plus d’informations, consultez [débogage du Code GPU](/visualstudio/debugger/debugging-gpu-code).  
  
- [Accelerator::direct3d_warp, données membres](reference/accelerator-class.md#direct3d_warp): cet accélérateur fournit une solution de secours pour l’exécution de code C++ AMP sur des processeurs multicœurs qui utilisent les Extensions Streaming SIMD (SSE).  
  
- [Accelerator::cpu_accelerator, données membres](reference/accelerator-class.md#cpu_accelerator): vous pouvez utiliser cet accélérateur de configuration des tableaux de mise en lots. Il ne peut pas exécuter le code C++ AMP. Pour plus d’informations, consultez la [mise en lots des tableaux en C++ AMP](http://go.microsoft.com/fwlink/p/?linkId=248485) publiez vos commentaires sur la programmation parallèle en Code natif blog.  
  
## <a name="interoperability"></a>Interopérabilité  
 Le runtime C++ AMP prend en charge l’interopérabilité entre le `accelerator_view` classe et le Direct3D [ID3D11Device interface](http://go.microsoft.com/fwlink/p/?linkId=248488). Le [create_accelerator_view](reference/concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view) méthode prend un `IUnknown` interface et retourne un `accelerator_view` objet. Le [get_device](http://msdn.microsoft.com/en-us/8194125e-8396-4d62-aa8a-65831dea8439) méthode prend un `accelerator_view` objet et retourne un `IUknown` interface.  
  
## <a name="see-also"></a>Voir aussi  
 [C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [Débogage du Code GPU](/visualstudio/debugger/debugging-gpu-code)   
 [accelerator_view, classe](../../parallel/amp/reference/accelerator-view-class.md)
