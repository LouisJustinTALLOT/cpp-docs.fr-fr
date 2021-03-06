---
description: 'En savoir plus sur : Comment : créer et utiliser des instances CComPtr et CComQIPtr'
title: 'Procédure : Créer et utiliser des instances CComPtr et CComQIPtr'
ms.custom: how-to
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: b0356cfb-12cc-4ee8-b988-8311ed1ab5e0
ms.openlocfilehash: c16d908e3df9e10641f1264aed7623463424de69
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97268650"
---
# <a name="how-to-create-and-use-ccomptr-and-ccomqiptr-instances"></a>Procédure : Créer et utiliser des instances CComPtr et CComQIPtr

En programmation Windows classique, les bibliothèques sont souvent implémentées en tant qu'objets COM (Component Object Model), ou plus précisément, en tant que serveurs COM. De nombreux composants du système d'exploitation Windows sont implémentés en tant que serveurs COM, et de nombreux collaborateurs fournissent des bibliothèques sous cette forme. Pour plus d’informations sur les bases du modèle COM, consultez [Component Object Model (COM)](/windows/win32/com/component-object-model--com--portal).

Lorsque vous instanciez un objet COM, enregistrez le pointeur d'interface dans un pointeur intelligent COM, qui effectue un décompte de références en utilisant des appels à `AddRef` et `Release` dans le destructeur. Si vous utilisez la bibliothèque ATL (Active Template Library) ou la bibliothèque MFC (Microsoft Foundation Class), utilisez le pointeur intelligent `CComPtr` . Si vous n'utilisez pas la bibliothèque ATL ou MFC, utilisez `_com_ptr_t`. Étant donné qu'aucun COM n'équivaut à `std::unique_ptr`, utilisez les pointeurs intelligents à la fois pour les scénarios à un seul propriétaire et ceux à plusieurs propriétaires. `CComPtr` et `ComQIPtr` prennent tous deux en charge les opérations de déplacement qui ont des références rvalue.

## <a name="example-ccomptr"></a>Exemple : CComPtr

L'exemple suivant montre comment utiliser `CComPtr` pour instancier un objet COM et obtenir des pointeurs sur ses interfaces. Notez que la fonction membre `CComPtr::CoCreateInstance` est utilisée pour créer l'objet COM, au lieu de la fonction Win32 qui porte le même nom.

[!code-cpp[COM_smart_pointers#01](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_1.cpp)]

`CComPtr` et ses parents font partie de la bibliothèque ATL et sont définis dans \<atlcomcli.h> . `_com_ptr_t` est déclaré dans \<comip.h> . Le compilateur crée des spécialisations de `_com_ptr_t` lorsqu'il génère des classes wrapper pour les bibliothèques de types.

## <a name="example-ccomqipt"></a>Exemple : CComQIPt

La bibliothèque ATL fournit également `CComQIPtr`, qui a une syntaxe plus simple pour interroger un objet COM en vue de récupérer une interface supplémentaire. Toutefois, nous vous recommandons `CComPtr` car il fait tout ce que `CComQIPtr` peut faire et est sémantiquement plus cohérent avec les pointeurs d'interface COM bruts. Si vous utilisez `CComPtr` pour effectuer une requête à une interface, le nouveau pointeur d'interface est placé dans un paramètre de sortie. Si l'appel échoue, un HRESULT est retourné, qui est le modèle COM standard. Avec `CComQIPtr`, la valeur retournée est le pointeur lui-même, et si l'appel échoue, la valeur de retour HRESULT interne est inaccessible. Les deux lignes suivantes indiquent comment les mécanismes de gestion des erreurs dans `CComPtr` et `CComQIPtr` diffèrent.

[!code-cpp[COM_smart_pointers#02](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_2.cpp)]

## <a name="example-idispatch"></a>Exemple : IDispatch

`CComPtr` fournit une spécialisation pour IDispatch qui lui permet de stocker les pointeurs vers les composants d'automation COM et d'appeler des méthodes sur l'interface à l'aide de la liaison tardive. `CComDispatchDriver` est un typedef pour `CComQIPtr<IDispatch, &IIDIDispatch>`, qui peut être converti implicitement en `CComPtr<IDispatch>`. Par conséquent, lorsque l'un de ces trois noms apparaît dans le code, il correspond à `CComPtr<IDispatch>`. L'exemple suivant montre comment obtenir un pointeur vers le modèle objet Microsoft Word en utilisant `CComPtr<IDispatch>`.

[!code-cpp[COM_smart_pointers#03](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_3.cpp)]

## <a name="see-also"></a>Voir aussi

[Pointeurs intelligents (Modern C++)](../cpp/smart-pointers-modern-cpp.md)
