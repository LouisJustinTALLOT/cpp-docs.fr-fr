---
title: 'Comment : créer et utiliser des Instances CComPtr et CComQIPtr | Documents Microsoft'
ms.custom: how-to
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b0356cfb-12cc-4ee8-b988-8311ed1ab5e0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6c63eb1657cd00580197e0571a40e9a7545688dd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32415450"
---
# <a name="how-to-create-and-use-ccomptr-and-ccomqiptr-instances"></a>Comment : créer et utiliser des instances CComPtr et CComQIPtr
En programmation Windows classique, les bibliothèques sont souvent implémentées en tant qu'objets COM (Component Object Model), ou plus précisément, en tant que serveurs COM. De nombreux composants du système d'exploitation Windows sont implémentés en tant que serveurs COM, et de nombreux collaborateurs fournissent des bibliothèques sous cette forme. Pour plus d’informations sur les bases du modèle COM, consultez [Component Object Model (COM)](http://msdn.microsoft.com/en-us/3578ca42-a4b6-44b3-ad5b-aeb5fa61f3f4).  
  
 Lorsque vous instanciez un objet COM, enregistrez le pointeur d'interface dans un pointeur intelligent COM, qui effectue un décompte de références en utilisant des appels à `AddRef` et `Release` dans le destructeur. Si vous utilisez la bibliothèque ATL (Active Template Library) ou la bibliothèque MFC (Microsoft Foundation Class), utilisez le pointeur intelligent `CComPtr` . Si vous n'utilisez pas la bibliothèque ATL ou MFC, utilisez `_com_ptr_t`. Étant donné qu'aucun COM n'équivaut à `std::unique_ptr`, utilisez les pointeurs intelligents à la fois pour les scénarios à un seul propriétaire et ceux à plusieurs propriétaires. `CComPtr` et `ComQIPtr` prennent tous deux en charge les opérations de déplacement qui ont des références rvalue.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment utiliser `CComPtr` pour instancier un objet COM et obtenir des pointeurs sur ses interfaces. Notez que la fonction membre `CComPtr::CoCreateInstance` est utilisée pour créer l'objet COM, au lieu de la fonction Win32 qui porte le même nom.  
  
 [!code-cpp[COM_smart_pointers#01](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_1.cpp)]  
  
 `CComPtr` et ses parents font partie de la bibliothèque ATL et sont définies dans \<atlcomcli.h >. `_com_ptr_t` est déclaré dans \<comip.h >. Le compilateur crée des spécialisations de `_com_ptr_t` lorsqu'il génère des classes wrapper pour les bibliothèques de types.  
  
## <a name="example"></a>Exemple  
 La bibliothèque ATL fournit également `CComQIPtr`, qui a une syntaxe plus simple pour interroger un objet COM en vue de récupérer une interface supplémentaire. Toutefois, nous vous recommandons `CComPtr` car il fait tout ce que `CComQIPtr` peut faire et est sémantiquement plus cohérent avec les pointeurs d'interface COM bruts. Si vous utilisez `CComPtr` pour effectuer une requête à une interface, le nouveau pointeur d'interface est placé dans un paramètre de sortie. Si l'appel échoue, un HRESULT est retourné, qui est le modèle COM standard. Avec `CComQIPtr`, la valeur retournée est le pointeur lui-même, et si l'appel échoue, la valeur de retour HRESULT interne est inaccessible. Les deux lignes suivantes indiquent comment les mécanismes de gestion des erreurs dans `CComPtr` et `CComQIPtr` diffèrent.  
  
 [!code-cpp[COM_smart_pointers#02](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_2.cpp)]  
  
## <a name="example"></a>Exemple  
 `CComPtr` fournit une spécialisation pour IDispatch qui lui permet de stocker les pointeurs vers les composants d'automation COM et d'appeler des méthodes sur l'interface à l'aide de la liaison tardive. `CComDispatchDriver` est un typedef pour `CComQIPtr<IDispatch, &IIDIDispatch>`, qui peut être converti implicitement en `CComPtr<IDispatch>`. Par conséquent, lorsque l'un de ces trois noms apparaît dans le code, il correspond à `CComPtr<IDispatch>`. L'exemple suivant montre comment obtenir un pointeur vers le modèle objet Microsoft Word en utilisant `CComPtr<IDispatch>`.  
  
 [!code-cpp[COM_smart_pointers#03](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_3.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Pointeurs intelligents](../cpp/smart-pointers-modern-cpp.md)