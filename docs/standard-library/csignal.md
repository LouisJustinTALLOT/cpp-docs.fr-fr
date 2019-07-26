---
title: '&lt;csignal&gt;'
ms.date: 11/04/2016
f1_keywords:
- <csignal>
helpviewer_keywords:
- csignal header
ms.assetid: d18bcf82-a89a-476c-a6bf-726af956f7c0
ms.openlocfilehash: 2e82877a54c433b9db638b908be290535b1cc857
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452331"
---
# <a name="ltcsignalgt"></a>&lt;csignal&gt;

Inclut l’en-tête \<signal. > h de la bibliothèque standard C et ajoute les noms associés à l' `std` espace de noms. L'inclusion de cet en-tête garantit également que les noms déclarés à l'aide d'une liaison externe dans l'en-tête de la bibliothèque C standard soient déclarés dans l'espace de noms `std`.


## <a name="syntax"></a>Syntaxe

```cpp
#include <csignal>
```

## <a name="namespace-and-macros"></a>Espace de noms et macros

```cpp
namespace std {
    using sig_atomic_t = see below;

    extern using signal-handler = void(int);
}

#define SIG_DFL
#define SIG_ERR
#define SIG_IGN
#define SIGABRT
#define SIGFPE
#define SIGILL
#define SIGINT
#define SIGSEGV
#define SIGTERM
```

## <a name="functions"></a>Fonctions

```cpp
signal-handler* signal(int sig, signal-handler* func);
int raise(int sig);
```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Vue d’ensemble de la bibliothèque C++ Standard](../standard-library/cpp-standard-library-overview.md)\
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
