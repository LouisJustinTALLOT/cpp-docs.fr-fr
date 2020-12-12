---
description: 'En savoir plus sur : constantes d’espace de noms d’accès concurrentiel (AMP)'
title: Concurrency, constantes de l’espace de noms (AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::HLSL_MAX_NUM_BUFFERS
- amp/Concurrency::MODULENAME_MAX_LENGTH
ms.assetid: 13a8e8cd-2eec-4e60-a91d-5d271072747b
ms.openlocfilehash: f8a2cd10aa2701bda24f7017704dce59c5609835
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122224"
---
# <a name="concurrency-namespace-constants-amp"></a>Concurrency, constantes de l’espace de noms (AMP)

[HLSL_MAX_NUM_BUFFERS](#hlsl_max_num_buffers)\
[MODULENAME_MAX_LENGTH](#modulename_max_length)

## <a name="hlsl_max_num_buffers-constant"></a><a name="hlsl_max_num_buffers"></a> Constante HLSL_MAX_NUM_BUFFERS

Nombre maximal de mémoires tampons autorisées par DirectX.

```cpp
static const UINT HLSL_MAX_NUM_BUFFERS = 64 + 128;
```

## <a name="modulename_max_length-constant"></a><a name="modulename_max_length"></a> Constante MODULENAME_MAX_LENGTH

Stocke la longueur maximale du nom du module. Cette valeur doit être la même sur le compilateur et le Runtime.

```cpp
static const UINT MODULENAME_MAX_LENGTH = 1024;
```

## <a name="see-also"></a>Voir aussi

[Concurrence de l’espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
