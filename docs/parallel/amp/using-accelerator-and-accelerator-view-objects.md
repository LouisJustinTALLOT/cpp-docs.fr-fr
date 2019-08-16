---
title: Utilisation des objets accelerator et accelerator_view
ms.date: 11/04/2016
ms.assetid: 18f0dc66-8236-4420-9f46-1a14f2c3fba1
ms.openlocfilehash: 80d9c26f636cc736f90eacddea07a8fc31caff93
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512886"
---
# <a name="using-accelerator-and-accelerator_view-objects"></a>Utilisation des objets accelerator et accelerator_view

Vous pouvez utiliser les classes [Accelerator](../../parallel/amp/reference/accelerator-class.md) et [accelerator_view](../../parallel/amp/reference/accelerator-view-class.md) pour spécifier l’appareil ou l’émulateur sur lequel C++ exécuter votre code amp. Un système peut avoir plusieurs appareils ou émulateurs qui diffèrent par la quantité de mémoire, la prise en charge de la mémoire partagée, la prise en charge du débogage ou la prise en charge de la double précision. C++Le programme amp (C++ Accelerated massive parallelism) fournit des API que vous pouvez utiliser pour examiner les accélérateurs disponibles, en définir un comme valeur par défaut, spécifier plusieurs accelerator_views pour les appels multiples à parallel_for_each et effectuer des tâches de débogage spéciales.

## <a name="using-the-default-accelerator"></a>Utilisation de l’accélérateur par défaut

Le C++ Runtime amp choisit un accélérateur par défaut, sauf si vous écrivez du code pour en sélectionner un spécifique. Le runtime choisit l’accélérateur par défaut comme suit:

1. Si l’application s’exécute en mode débogage, il s’agit d’un accélérateur qui prend en charge le débogage.

2. Dans le cas contraire, l’accélérateur spécifié par la variable d’environnement CPPAMP_DEFAULT_ACCELERATOR, s’il est défini.

3. Dans le cas contraire, un appareil non émulé.

4. Dans le cas contraire, l’appareil qui dispose de la plus grande quantité de mémoire disponible.

5. Dans le cas contraire, il s’agit d’un appareil qui n’est pas attaché à l’affichage.

En outre, le runtime spécifie `access_type` un `access_type_auto` de pour l’accélérateur par défaut. Cela signifie que l’accélérateur par défaut utilise la mémoire partagée si elle est prise en charge et si ses caractéristiques de performances (bande passante et latence) sont connues pour être identiques à la mémoire dédiée (non partagée).

Vous pouvez déterminer les propriétés de l’accélérateur par défaut en construisant l’accélérateur par défaut et en examinant ses propriétés. L’exemple de code suivant imprime le chemin d’accès, la quantité de mémoire accélérateur, la prise en charge de la mémoire partagée, la prise en charge de la double précision et la prise en charge de la double précision limitée de l’accélérateur par défaut.

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

### <a name="cppamp_default_accelerator-environment-variable"></a>Variable d’environnement CPPAMP_DEFAULT_ACCELERATOR

Vous pouvez définir la variable d’environnement CPPAMP_DEFAULT_ACCELERATOR pour spécifier `accelerator::device_path` le de l’accélérateur par défaut. Le chemin d’accès dépend du matériel. Le code suivant utilise la `accelerator::get_all` fonction pour récupérer une liste des accélérateurs disponibles, puis affiche le chemin d’accès et les caractéristiques de chaque accélérateur.

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

Pour sélectionner un accélérateur, utilisez la `accelerator::get_all` méthode pour récupérer une liste des accélérateurs disponibles, puis sélectionnez-en un en fonction de ses propriétés. Cet exemple montre comment sélectionner l’accélérateur qui a le plus de mémoire:

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
> L’un des accélérateurs retournés par `accelerator::get_all` est l’accélérateur de l’UC. Vous ne pouvez pas exécuter du code sur l’accélérateur d’UC. Pour filtrer l’accélérateur de l’UC, comparez la valeur de la propriété [device_path](reference/accelerator-class.md#device_path) de l’accélérateur retourné par `accelerator::get_all` avec la valeur de l' [accélérateur:: cpu_accelerator](reference/accelerator-class.md#cpu_accelerator). Pour plus d’informations, consultez la section «accélérateurs spéciaux» de cet article.

## <a name="shared-memory"></a>Mémoire partagée

La mémoire partagée est une mémoire accessible à la fois par l’UC et l’accélérateur. L’utilisation de la mémoire partagée permet d’éliminer ou de réduire considérablement la surcharge liée à la copie de données entre l’UC et l’accélérateur. Bien que la mémoire soit partagée, elle ne peut pas être accessible simultanément à la fois par l’UC et l’accélérateur, ce qui entraîne un comportement indéfini. La propriété d’accélérateur [supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory) retourne la **valeur true** si l’accélérateur prend en charge la mémoire partagée, et la propriété [default_cpu_access_type](reference/accelerator-class.md#default_cpu_access_type) obtient le [access_type](reference/concurrency-namespace-enums-amp.md#access_type) par défaut pour la mémoire allouée sur le `accelerator`(par exemple, **tableau**s `accelerator`associés aux objets, ou `array_view` accessibles sur le `accelerator`.

Le C++ Runtime amp choisit automatiquement la valeur par `access_type` défaut la `accelerator`plus appropriée pour chaque, mais les caractéristiques de performance (bande passante et latence) de la mémoire partagée peuvent être pires que celles de la mémoire d’accélérateur dédiée (non partagée) quand lecture à partir du processeur, écriture à partir du processeur, ou les deux. Si la mémoire partagée fonctionne aussi bien que la mémoire dédiée pour la lecture et l’écriture à partir de l’UC `access_type_read_write`, le runtime prend la valeur par défaut; sinon `access_type`, le runtime choisit une valeur par défaut plus restrictive et autorise l’application à la substituer si l’accès à la mémoire les modèles de ses noyaux de calcul bénéficient d’un `access_type`autre.

L’exemple de code suivant montre comment déterminer si l’accélérateur par défaut prend en charge la mémoire partagée, puis substitue son type d’accès par `accelerator_view` défaut et en crée un à partir de celui-ci.

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

Un `accelerator_view` reflète toujours le `default_cpu_access_type` du `accelerator` associé à et ne fournit aucune interface pour remplacer ou modifier son `access_type`.

## <a name="changing-the-default-accelerator"></a>Modification de l’accélérateur par défaut

Vous pouvez modifier l’accélérateur par défaut en appelant `accelerator::set_default` la méthode. Vous ne pouvez modifier l’accélérateur par défaut qu’une seule fois par exécution d’application et vous devez le modifier avant d’exécuter du code sur le GPU. Tous les appels de fonction suivants pour changer l’accélérateur renvoient la **valeur false**. Si vous souhaitez utiliser un autre accélérateur dans un appel à `parallel_for_each`, consultez la section «utilisation de plusieurs accélérateurs» dans cet article. L’exemple de code suivant affecte à l’accélérateur par défaut une valeur qui n’est pas émulée, n’est pas connecté à un affichage et prend en charge la double précision.

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

## <a name="using-multiple-accelerators"></a>Utilisation de plusieurs accélérateurs

Il existe deux façons d’utiliser plusieurs accélérateurs dans votre application:

- Vous pouvez passer `accelerator_view` des objets aux appels à la méthode [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) .

- Vous pouvez construire un objet **tableau** à l’aide `accelerator_view` d’un objet spécifique. Le Runtime C + amp récupère l' `accelerator_view` objet de l’objet **tableau** capturé dans l’expression lambda.

## <a name="special-accelerators"></a>Accélérateurs spéciaux

Les chemins d’accès de l’appareil de trois accélérateurs spéciaux sont disponibles `accelerator` en tant que propriétés de la classe:

- [accélérateur::D membre de données irect3d_ref](reference/accelerator-class.md#direct3d_ref): Cet accélérateur à thread unique utilise le logiciel sur le processeur pour émuler une carte graphique générique. Elle est utilisée par défaut pour le débogage, mais elle n’est pas utile en production, car elle est plus lente que les accélérateurs matériels. En outre, il est disponible uniquement dans le kit de développement logiciel (SDK) DirectX et le SDK Windows, et il est peu probable qu’il soit installé sur les ordinateurs de vos clients. Pour plus d’informations, consultez Débogage du [code GPU](/visualstudio/debugger/debugging-gpu-code).

- [accélérateur::D membre de données irect3d_warp](reference/accelerator-class.md#direct3d_warp): Cet accélérateur fournit une solution de secours pour l' C++ exécution de code amp sur des processeurs multicœurs qui utilisent des extensions streaming SIMD (SSE).

- [membre de données Accelerator:: cpu_accelerator](reference/accelerator-class.md#cpu_accelerator): Vous pouvez utiliser cet accélérateur pour configurer des groupes de mise en lots. Il ne peut C++ pas exécuter de code amp. Pour plus d’informations, consultez les [tableaux intermédiaires dans C++ amp](https://blogs.msdn.microsoft.com/nativeconcurrency/2011/11/09/staging-arrays-in-c-amp/) poster sur le blog programmation parallèle en code natif.

## <a name="interoperability"></a>Interopérabilité

Le C++ Runtime amp prend en charge l’interopérabilité entre la `accelerator_view` classe et l’interface Direct3D [ID3D11Device](/windows/win32/api/d3d11/nn-d3d11-id3d11device). La méthode [create_accelerator_view](reference/concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view) prend une `IUnknown` interface et retourne un `accelerator_view` objet. La méthode [get_device](reference/concurrency-direct3d-namespace-functions-amp.md#get_device) prend un `accelerator_view` objet et retourne une `IUnknown` interface.

## <a name="see-also"></a>Voir aussi

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[Débogage du code GPU](/visualstudio/debugger/debugging-gpu-code)<br/>
[accelerator_view, classe](../../parallel/amp/reference/accelerator-view-class.md)
