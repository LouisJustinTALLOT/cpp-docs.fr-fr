---
title: Référence (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::Reference (C++ AMP)
helpviewer_keywords:
- C++ Accelerated Massive Parallelism, reference
ms.assetid: 372a8aed-8a53-48c9-996f-9c3cf09c9fa8
ms.openlocfilehash: 5e6905adee6e6cad0c0c49488352f4a039aa27eb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630055"
---
# <a name="reference-c-amp"></a>Référence (C++ AMP)

Cette section contient des informations de référence pour le runtime C++ Accelerated les Massive Parallelism (C++ AMP).

> [!NOTE]
>  La norme du langage C++ réserve l’utilisation des identificateurs commençant par un caractère de soulignement (`_`) aux implémentations telles que les bibliothèques. N’utilisez donc pas de noms commençant par un trait de soulignement dans votre code. Le comportement des éléments de code, dont les noms suivent cette convention n'est pas garanti et est susceptible de changer dans les futures mises à jour. Pour ces raisons, ces éléments de code ont été omis de cette documentation.

## <a name="in-this-section"></a>Dans cette section

[Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)<br/>
Fournit des classes et des fonctions qui permettent l’accélération du code C++ sur matériel parallèle de données.

[Concurrency::direct3d, espace de noms](concurrency-direct3d-namespace.md)<br/>
Fournit des fonctions qui prennent en charge l’interopérabilité D3D. Permet une utilisation transparente les ressources D3D pour le calcul dans le code AMP et l’utilisation des ressources créées dans AMP dans le code D3D, sans créer de copies intermédiaires redondantes. Vous pouvez utiliser C++ AMP pour accélérer de façon incrémentielle les sections intensives de vos applications DirectX et utiliser l’API D3D sur les données générées par des calculs AMP.

[Concurrency::fast_math, espace de noms](concurrency-fast-math-namespace.md)<br/>
Fonctions dans le `fast_math` espace de noms ne sont pas conformes C99. Seules les versions de simple précision de chaque fonction sont fournies. Ces fonctions utilisent les fonctions intrinsèques DirectX, qui sont plus rapides que les fonctions correspondantes dans le `precise_math` espace de noms et ne nécessitent pas de prise en charge de double précision étendue sur l’accélérateur, mais elles sont moins précises. Il existe deux versions de chaque fonction pour la compatibilité au niveau de la source avec le code C99 ; les deux versions prennent et retournent des valeurs de simple précision.

[Concurrency::graphics, espace de noms](concurrency-graphics-namespace.md)<br/>
Fournit des types et fonctions qui sont conçues pour la programmation graphique.

[Concurrency::precise_math, espace de noms](concurrency-precise-math-namespace.md)<br/>
Fonctions dans le `precise_math` espace de noms sont conformes C99. Versions simple précision et double précision de chaque fonction sont incluses. Ces fonctions, cela inclut les fonctions simple précision, requièrent une prise en charge double précision étendue sur l’accélérateur.

## <a name="related-sections"></a>Rubriques connexes

[C++ AMP (C++ Accelerated Massive Parallelism)](../../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
C++ AMP accélère l’exécution de votre code C++ en tirant parti du matériel parallèle de données qui est plus communément présent en tant qu’une unité de traitement graphique (GPU) sur une carte graphique distincte.

