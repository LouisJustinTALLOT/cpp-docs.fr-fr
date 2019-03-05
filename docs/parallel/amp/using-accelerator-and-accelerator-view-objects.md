---
title: Utilisation des objets accelerator et accelerator_view
ms.date: 11/04/2016
ms.assetid: 18f0dc66-8236-4420-9f46-1a14f2c3fba1
ms.openlocfilehash: 05ca53d075867fefa43f7471bb795040d075274e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272896"
---
# <a name="using-accelerator-and-acceleratorview-objects"></a>Utilisation des objets accelerator et accelerator_view

Vous pouvez utiliser la [accelerator](../../parallel/amp/reference/accelerator-class.md) et [accelerator_view](../../parallel/amp/reference/accelerator-view-class.md) pour spécifier le périphérique ou l’émulateur pour exécuter votre code C++ AMP sur les classes. Un système peut avoir plusieurs périphériques ou émulateurs qui varient selon la quantité de mémoire, de prise en charge de la mémoire partagée, de prise en charge de débogage ou de prise en charge double précision. C++ Accelerated les Massive Parallelism (C++ AMP) fournit des API que vous pouvez utiliser pour examiner les accélérateurs disponibles, définir un comme la valeur par défaut, spécifier plusieurs accelerator_views pour plusieurs appels au parallel_for_each et effectuer des tâches spéciales de débogage.

## <a name="using-the-default-accelerator"></a>À l’aide de l’accélérateur par défaut

Le runtime C++ AMP choisit un accélérateur par défaut, sauf si vous écrivez du code permettant de sélectionner une valeur spécifique. Le runtime sélectionne l’accélérateur par défaut comme suit :

1. Si l’application s’exécute en mode débogage, un accélérateur qui prend en charge le débogage.

2. Dans le cas contraire, l’accélérateur spécifié par l’environnement de cppamp_default_accelerator, si elle est définie.

3. Sinon, un périphérique non émulé.

4. Sinon, l’appareil qui a la plus grande quantité de mémoire disponible.

5. Sinon, un appareil qui n’est pas attaché à l’affichage.

En outre, le runtime spécifie un `access_type` de `access_type_auto` pour l’accélérateur par défaut. Cela signifie que l’accélérateur par défaut utilise la mémoire partagée si elle est prise en charge et si ses caractéristiques de performance (bande passante et latence) sont connus pour être le même que de mémoire dédiée (non partagée).

Vous pouvez déterminer les propriétés de l’accélérateur par défaut en construisant l’accélérateur par défaut et en examinant ses propriétés. L’exemple de code suivant imprime le chemin d’accès, quantité de mémoire d’accélérateur, prise en charge de la mémoire partagée, prise en charge double précision et une prise en charge double précision limitée de l’accélérateur par défaut.

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

### <a name="cppampdefaultaccelerator-environment-variable"></a>Environnement Cppamp_default_accelerator

Vous pouvez définir l’environnement de cppamp_default_accelerator pour spécifier le `accelerator::device_path` de l’accélérateur par défaut. Le chemin d’accès dépend du matériel. Le code suivant utilise la `accelerator::get_all` fonction pour récupérer la liste des accélérateurs disponibles, puis affiche le chemin d’accès et les caractéristiques de chaque accélérateur.

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

Pour sélectionner un accélérateur, utilisez le `accelerator::get_all` méthode pour récupérer la liste des accélérateurs disponibles, puis sélectionnez un selon ses propriétés. Cet exemple montre comment choisir l’accélérateur ayant le plus de mémoire :

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
> Un des accélérateurs retournés par `accelerator::get_all` est l’accélérateur d’UC. Vous ne pouvez pas exécuter du code sur l’accélérateur d’UC. Pour filtrer l’accélérateur d’UC, comparez la valeur de la [device_path](reference/accelerator-class.md#device_path) propriété de l’accélérateur retourné par `accelerator::get_all` avec la valeur de la [accelerator::cpu_accelerator](reference/accelerator-class.md#cpu_accelerator). Pour plus d’informations, consultez la section « Accélérateurs spéciaux » dans cet article.

## <a name="shared-memory"></a>Mémoire partagée

Mémoire partagée est la mémoire qui est accessible par le processeur et de l’accélérateur. L’utilisation de la mémoire partagée élimine ou réduit considérablement la surcharge de copie des données entre l’UC et de l’accélérateur. Bien que la mémoire est partagée, il ne peut pas être accessibles simultanément par le processeur et de l’accélérateur, et cela entraîne un comportement non défini. La propriété d’un accélérateur [supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory) retourne **true** si l’accélérateur prend en charge la mémoire partagée et le [default_cpu_access_type](reference/accelerator-class.md#default_cpu_access_type) Set de propriété la valeur par défaut [access_type](reference/concurrency-namespace-enums-amp.md#access_type) pour la mémoire allouée sur le `accelerator`— par exemple, **tableau**s associé à la `accelerator`, ou `array_view` objets ouvertes sur le `accelerator`.

Le runtime C++ AMP choisit automatiquement la meilleure option par défaut `access_type` pour chaque `accelerator`, mais les caractéristiques de performance (bande passante et latence) de mémoire partagée peuvent être pires que celles de la mémoire d’accélérateur dédiée de (non partagée) lors de la lecture à partir de l’UC, écriture à partir de l’UC, ou les deux. Si la mémoire partagée s’exécute, ainsi que la mémoire dédiée pour la lecture et écriture à partir de l’UC, le runtime par défaut est `access_type_read_write`; sinon, le runtime choisit une valeur par défaut plus conservateur `access_type`et autorise l’application à remplacer si accéder à la mémoire modèles de ses cœurs de calcul en bénéficier une autre `access_type`.

L’exemple de code suivant montre comment déterminer si l’accélérateur par défaut prend en charge de la mémoire partagée, puis substitue son type d’accès par défaut et crée un `accelerator_view` à partir de celui-ci.

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

Un `accelerator_view` reflète toujours le `default_cpu_access_type` de la `accelerator` lui est associée, et il ne fournit aucune interface pour substituer ou modifier ses `access_type`.

## <a name="changing-the-default-accelerator"></a>Modification de l’accélérateur par défaut

Vous pouvez modifier l’accélérateur par défaut en appelant le `accelerator::set_default` (méthode). Vous pouvez modifier l’accélérateur par défaut une seule fois par application l’exécution et vous devez le modifier avant n’importe quel code est exécuté sur le GPU. Retournent tous les appels de fonction suivants à modifier l’accélérateur **false**. Si vous souhaitez utiliser un accélérateur différent dans un appel à `parallel_for_each`, lisez la section « Utilisation de plusieurs accélérateurs » dans cet article. L’exemple de code suivant définit l’accélérateur par défaut pour qu’il n’est pas émulée, n’est pas connecté à un affichage et prend en charge double précision.

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

Il existe deux façons d’utiliser plusieurs accélérateurs dans votre application :

- Vous pouvez transmettre `accelerator_view` objets à des appels à la [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) (méthode).

- Vous pouvez construire un **tableau** à l’aide d’un spécifique de l’objet `accelerator_view` objet. Le runtime C + AMP prendra le `accelerator_view` objet capturées **tableau** objet dans l’expression lambda.

## <a name="special-accelerators"></a>Accélérateurs spéciaux

Les chemins d’accès de périphérique de trois accélérateurs spéciaux sont disponibles en tant que propriétés de la `accelerator` classe :

- [Accelerator::direct3d_ref, données membres](reference/accelerator-class.md#direct3d_ref): Cet accélérateur monothread utilise des logiciels sur le CPU pour émuler une carte graphique générique. Il est utilisé par défaut pour le débogage, mais il n’est pas utile dans la production, car il est plus lent que les accélérateurs matériels. En outre, il est disponible uniquement dans le SDK DirectX et le Kit de développement Windows, et il est peu susceptible d’être installé sur les ordinateurs de vos clients. Pour plus d’informations, consultez [débogage du Code GPU](/visualstudio/debugger/debugging-gpu-code).

- [Accelerator::direct3d_warp, données membres](reference/accelerator-class.md#direct3d_warp): Cet accélérateur fournit une solution de secours pour l’exécution de code C++ AMP sur les processeurs multicœurs qui utilisent des Extensions Streaming SIMD (SSE).

- [Accelerator::cpu_accelerator, données membres](reference/accelerator-class.md#cpu_accelerator): Vous pouvez utiliser cet accélérateur pour installer des tableaux temporaires. Il ne peut pas exécuter du code C++ AMP. Pour plus d’informations, consultez le [tableaux temporaires dans C++ AMP](https://blogs.msdn.microsoft.com/nativeconcurrency/2011/11/09/staging-arrays-in-c-amp/) publier sur la programmation parallèle en Code natif blog.

## <a name="interoperability"></a>Interopérabilité

Le runtime C++ AMP prend en charge l’interopérabilité entre le `accelerator_view` classe et le Direct3D [ID3D11Device interface](/windows/desktop/api/d3d11/nn-d3d11-id3d11device). Le [create_accelerator_view](reference/concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view) méthode prend un `IUnknown` interface et retourne un `accelerator_view` objet. Le [get_device](reference/concurrency-direct3d-namespace-functions-amp.md#get_device) méthode prend un `accelerator_view` objet et retourne un `IUnknown` interface.

## <a name="see-also"></a>Voir aussi

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[Débogage du code GPU](/visualstudio/debugger/debugging-gpu-code)<br/>
[accelerator_view, classe](../../parallel/amp/reference/accelerator-view-class.md)
