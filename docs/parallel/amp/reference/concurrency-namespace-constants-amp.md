---
title: Concurrency, constantes de l’espace de noms (AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::HLSL_MAX_NUM_BUFFERS
- amp/Concurrency::MODULENAME_MAX_LENGTH
ms.assetid: 13a8e8cd-2eec-4e60-a91d-5d271072747b
ms.openlocfilehash: d719878e67855bc513e25702b7100e9db731b3ff
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376375"
---
# <a name="concurrency-namespace-constants-amp"></a>Concurrency, constantes de l’espace de noms (AMP)

|||
|-|-|
|[HLSL_MAX_NUM_BUFFERS](#hlsl_max_num_buffers)|[MODULENAME_MAX_LENGTH](#modulename_max_length)|

## <a name="hlsl_max_num_buffers-constant"></a><a name="hlsl_max_num_buffers"></a>HLSL_MAX_NUM_BUFFERS Constant

Le nombre maximum de tampons autorisés par DirectX.

```cpp
static const UINT HLSL_MAX_NUM_BUFFERS = 64 + 128;
```

## <a name="modulename_max_length-constant"></a><a name="modulename_max_length"></a>MODULENAME_MAX_LENGTH Constant

Stocke la longueur maximale du nom du module. Cette valeur doit être la même sur le compilateur et l’heure d’exécution.

```cpp
static const UINT MODULENAME_MAX_LENGTH = 1024;
```

## <a name="see-also"></a>Voir aussi

[Concurrency Namespace (AMP)](concurrency-namespace-cpp-amp.md)
