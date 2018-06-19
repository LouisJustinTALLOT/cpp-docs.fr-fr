---
title: threadprivate | Documents Microsoft
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
ms.openlocfilehash: e7e7edaa36f929750087e3c81f42204ff20e9f62
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692910"
---
# <a name="threadprivate"></a>threadprivate
Spécifie qu’une variable privée à un thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma omp threadprivate(var)  
```  
  
## <a name="remarks"></a>Notes  
 où,  
  
 `var`  
 Une liste séparée par des virgules de variables que vous souhaitez rendre privé à un thread. `var` doit être une variable globale ou espace de noms-étendue ou une variable statique locale.  
  
## <a name="remarks"></a>Notes  
 Le `threadprivate` directive prend en charge aucune clauses OpenMP.  
  
 Pour plus d’informations, consultez [2.7.1 Directive threadprivate](../../../parallel/openmp/2-7-1-threadprivate-directive.md).  
  
 Le `threadprivate` la directive est basée sur le [thread](../../../cpp/thread.md) `__declspec` attribut ; limites sur **__declspec (thread)** s’appliquent à `threadprivate`.  
  
 Vous ne pouvez pas utiliser `threadprivate` dans n’importe quelle DLL qui sera chargé via [LoadLibrary](http://msdn.microsoft.com/library/windows/desktop/ms684175).  Cela inclut les DLL qui sont chargées avec [DELAYLOAD (délai de chargement de l’importation)](../../../build/reference/delayload-delay-load-import.md), qui utilise également **LoadLibrary**.  
  
 Vous pouvez utiliser `threadprivate` dans une DLL est chargée statiquement au démarrage du processus.  
  
 Étant donné que `threadprivate` est basée sur **__declspec (thread)**, un `threadprivate` variable existe dans n’importe quel thread a démarré dans le processus, pas seulement les threads qui font partie d’une équipe de thread générée par une région parallèle.  Il s’agit d’un détail d’implémentation que vous pouvez connaître, étant donné que vous pouvez remarquer, par exemple, les constructeurs pour un `threadprivate` type défini par l’utilisateur appelée plus souvent puis attendu.  
  
 A `threadprivate` variable d’un type destructable n’est pas garantie pour que son destructeur appelé.  Par exemple :  
  
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
  
 Les utilisateurs n’ont aucun contrôle lorsque les threads constituant la région parallèle va se terminer.  Si ces threads existent lorsque le processus s’arrête, les threads ne seront pas informés sur la sortie du processus et le destructeur ne sera pas appelé pour `threaded_var` sur n’importe quel thread à l’exception de celui qui se termine (ici, le thread principal).  Pour le code ne doit pas compter sur la destruction correcte de `threadprivate` variables.  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple d’utilisation de `threadprivate`, consultez [privé](../../../parallel/openmp/reference/private-openmp.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)