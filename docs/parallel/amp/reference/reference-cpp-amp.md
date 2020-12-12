---
description: 'En savoir plus sur : référence (C++ AMP)'
title: Référence (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::Reference (C++ AMP)
helpviewer_keywords:
- C++ Accelerated Massive Parallelism, reference
ms.assetid: 372a8aed-8a53-48c9-996f-9c3cf09c9fa8
ms.openlocfilehash: 043522d7524078c3c7fec956021fdd7a86347169
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327636"
---
# <a name="reference-c-amp"></a>Référence (C++ AMP)

Cette section contient des informations de référence sur le runtime de C++ Accelerated Massive Parallelism (C++ AMP).

> [!NOTE]
> La norme du langage C++ réserve l’utilisation des identificateurs commençant par un caractère de soulignement (`_`) aux implémentations telles que les bibliothèques. N’utilisez donc pas de noms commençant par un trait de soulignement dans votre code. Le comportement des éléments de code, dont les noms suivent cette convention n'est pas garanti et est susceptible de changer dans les futures mises à jour. Pour ces raisons, ces éléments de code ont été omis de cette documentation.

## <a name="in-this-section"></a>Dans cette section

[Concurrence de l’espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)<br/>
Fournit des classes et des fonctions qui permettent l’accélération du code C++ sur le matériel parallèle de données.

[Concurrency::direct3d, espace de noms](concurrency-direct3d-namespace.md)<br/>
Fournit des fonctions qui prennent en charge l’interopérabilité D3D. Permet l’utilisation transparente des ressources D3D pour le calcul dans le code AMP et l’utilisation des ressources créées dans AMP dans le code D3D, sans créer de copies intermédiaires redondantes. Vous pouvez utiliser C++ AMP pour accélérer de manière incrémentielle les sections de calcul intensif de vos applications DirectX et utiliser l’API D3D sur les données générées à partir de calculs AMP.

[Concurrency::fast_math, espace de noms](concurrency-fast-math-namespace.md)<br/>
Les fonctions de l' `fast_math` espace de noms ne sont pas conformes à C99. Seules les versions à simple précision de chaque fonction sont fournies. Ces fonctions utilisent les fonctions intrinsèques DirectX, qui sont plus rapides que les fonctions correspondantes dans l' `precise_math` espace de noms et ne nécessitent pas de prise en charge de la double précision étendue sur l’accélérateur, mais elles sont moins précises. Il existe deux versions de chaque fonction pour la compatibilité au niveau de la source avec le code C99 ; les deux versions prennent et retournent des valeurs à simple précision.

[Concurrency::graphics, espace de noms](concurrency-graphics-namespace.md)<br/>
Fournit des types et des fonctions conçus pour la programmation graphique.

[Concurrence ::p espace de noms recise_math](concurrency-precise-math-namespace.md)<br/>
Les fonctions de l' `precise_math` espace de noms sont conformes à C99. Les versions à simple précision et à double précision de chaque fonction sont incluses. Ces fonctions incluent les fonctions à simple précision, nécessitent une prise en charge étendue de la double précision sur l’accélérateur.

## <a name="related-sections"></a>Sections connexes

[C++ AMP (C++ Accelerated Massive Parallelism)](../../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
C++ AMP accélère l’exécution de votre code C++ en tirant parti du matériel parallèle de données qui est couramment présent en tant qu’unité de traitement graphique (GPU) sur une carte graphique discrète.
