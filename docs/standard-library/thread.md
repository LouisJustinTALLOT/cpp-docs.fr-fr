---
title: '&lt;thread&gt; | Documents Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <thread>
dev_langs:
- C++
ms.assetid: 0c858405-4efb-449d-bf76-70d3693c9234
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 496269689428e73dc78893092844afb1650da20d
ms.contentlocale: fr-fr
ms.lasthandoff: 04/29/2017

---
# <a name="ltthreadgt"></a>&lt;thread&gt;
Incluez l’en-tête standard \<thread > pour définir la classe `thread` et diverses fonctions de prise en charge.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
#include <thread>  
```  
  
## <a name="remarks"></a>Remarques  
  
> [!NOTE]
>  Dans le code est compilé à l’aide de **/CLR**, cet en-tête est bloqué.  
  
 Le `__STDCPP_THREADS__` macro est défini comme une valeur différente de zéro pour indiquer que les threads sont pris en charge par cet en-tête.  
  
## <a name="members"></a>Membres  
  
### <a name="public-classes"></a>Classes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[thread, classe](../standard-library/thread-class.md)|Définit un objet qui sert à observer et de gérer un thread d’exécution dans une application.|  
  
### <a name="public-structures"></a>Structures publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[hash, structure (bibliothèque standard C++)](../standard-library/hash-structure-stl.md)|Définit une fonction membre qui retourne une valeur qui est déterminée de manière unique par un `thread::id`. La fonction membre définit un [hachage](../standard-library/hash-class.md) fonction qui est appropriée pour les valeurs de mappage de type `thread::id` pour une distribution de valeurs d’index.|  
  
### <a name="public-functions"></a>Fonctions publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[get_id](../standard-library/thread-functions.md#get_id)|Identifie de façon unique le thread d’exécution en cours.|  
|[sleep_for](../standard-library/thread-functions.md#sleep_for)|Bloque le thread appelant.|  
|[sleep_until](../standard-library/thread-functions.md#sleep_until)|Bloque le thread appelant au moins jusqu’à l’heure spécifiée.|  
|[swap](../standard-library/thread-functions.md#swap)|Échange les États de deux `thread` objets.|  
|[yield](../standard-library/thread-functions.md#yield)|Indique au système d’exploitation d’exécuter d’autres threads, même si le thread actuel continuerait normalement à s’exécuter.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[opérateur > = (opérateur)](../standard-library/thread-operators.md#op_gt_eq)|Détermine si un objet `thread::id` est supérieur ou égal à un autre.|  
|[opérateur > (opérateur)](../standard-library/thread-operators.md#op_gt)|Détermine si un objet `thread::id` est supérieur à un autre.|  
|[opérateur < = (opérateur)](../standard-library/thread-operators.md#op_lt_eq)|Détermine si un objet `thread::id` est inférieur ou égal à un autre.|  
|[opérateur < (opérateur)](../standard-library/thread-operators.md#op_lt)|Détermine si un objet `thread::id` est inférieur à un autre.|  
|[opérateur ! =, opérateur](../standard-library/thread-operators.md#op_neq)|Compare deux objets `thread::id` pour déterminer s'ils sont différents.|  
|[opérateur == (opérateur)](../standard-library/thread-operators.md#op_eq_eq)|Compare deux objets `thread::id` pour déterminer s’ils sont égaux.|  
|[opérateur << (opérateur)](../standard-library/thread-operators.md#op_lt_lt)|Insère une représentation textuelle d’un objet `thread::id` dans un flux.|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)   
 [Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)


