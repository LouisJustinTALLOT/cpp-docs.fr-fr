---
title: threadprivate | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- threadprivate
dev_langs:
- C++
helpviewer_keywords:
- threadprivate OpenMP directive
ms.assetid: 3515aaed-6f9d-4d59-85eb-342378bea2d3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a9313934744f6eae66736f25b0d0b8592743cf12
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46376978"
---
# <a name="threadprivate"></a>threadprivate

Spécifie qu’une variable est privée pour un thread.

## <a name="syntax"></a>Syntaxe

```
#pragma omp threadprivate(var)
```

### <a name="parameters"></a>Paramètres

*var*<br/>
Une liste séparée par des virgules des variables que vous souhaitez rendre privé à un thread. `var` doit être une variable globale ou espace de noms-portée ou une variable locale statique.

## <a name="remarks"></a>Notes

Le `threadprivate` directive prend en charge aucune clause OpenMP.

Pour plus d’informations, consultez [2.7.1 Directive threadprivate](../../../parallel/openmp/2-7-1-threadprivate-directive.md).

Le `threadprivate` directive est basée sur le [thread](../../../cpp/thread.md) `__declspec` attribut ; limites sur **__declspec (thread)** s’appliquent à `threadprivate`.

Vous ne pouvez pas utiliser `threadprivate` dans n’importe quelle DLL qui est chargée par le biais de [LoadLibrary](https://msdn.microsoft.com/library/windows/desktop/ms684175).  Cela inclut les DLL qui sont chargées avec [/DELAYLOAD (différer le chargement l’importation)](../../../build/reference/delayload-delay-load-import.md), qui utilise également **LoadLibrary**.

Vous pouvez utiliser `threadprivate` dans une DLL est chargée statiquement au démarrage du processus.

Étant donné que `threadprivate` repose sur **__declspec (thread)**, un `threadprivate` variable existera dans n’importe quel thread a démarré le processus, pas seulement les threads qui font partie d’une équipe de thread générée par une région parallèle.  Il s’agit d’un détail d’implémentation que vous pouvez connaître, étant donné que vous pouvez remarquer, par exemple, les constructeurs pour un `threadprivate` type défini par l’utilisateur appelée plus souvent puis attendu.

A `threadprivate` variable d’un type destructable n’est pas garanti d’avoir son destructeur appelé.  Exemple :

```
struct MyType
{
    ~MyType();
};

MyType threaded_var;
#pragma omp threadprivate(threaded_var)
int main()
{
    #pragma omp parallel
    {}
}
```

Les utilisateurs n’ont aucun contrôle quant à lorsque les threads qui constituent la région parallèle seront termine.  Si ces threads existent lorsque le processus se termine, les threads ne pas être informés sur la sortie du processus, et le destructeur ne sera pas appelé pour `threaded_var` sur n’importe quel thread à l’exception de celui qui se termine (ici, le thread principal).  Afin de code ne doit pas compter sur la destruction correcte de `threadprivate` variables.

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `threadprivate`, consultez [privé](../../../parallel/openmp/reference/private-openmp.md).

## <a name="see-also"></a>Voir aussi

[Directives](../../../parallel/openmp/reference/openmp-directives.md)