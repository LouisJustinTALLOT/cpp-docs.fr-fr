---
title: _com_ptr_t, classe
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t
helpviewer_keywords:
- _com_ptr_t class
ms.assetid: 3753a8a0-03d4-4cfd-8a9a-74872ea53971
ms.openlocfilehash: 2c299ea4a5aaabba847c85500a6023d7b112d492
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838501"
---
# <a name="_com_ptr_t-class"></a>_com_ptr_t, classe

**Spécifique à Microsoft**

Un objet **_com_ptr_t** encapsule un pointeur d’interface com et est appelé pointeur « intelligent ». Cette classe de modèle gère l’allocation et la désallocation des ressources via des appels de fonction aux `IUnknown` fonctions membres : `QueryInterface` , `AddRef` et `Release` .

Un pointeur intelligent est généralement référencé par la définition de typedef fournie par la macro _COM_SMARTPTR_TYPEDEF. Cette macro accepte un nom d’interface et l’IID, et déclare une spécialisation de **_com_ptr_t** avec le nom de l’interface plus un suffixe `Ptr` . Par exemple :

```cpp
_COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
```

déclare la spécialisation **_com_ptr_t** `IMyInterfacePtr` .

Un jeu de [modèles de fonction](../cpp/relational-function-templates.md), et non des membres de cette classe de modèle, prend en charge les comparaisons avec un pointeur intelligent à droite de l’opérateur de comparaison.

### <a name="construction"></a>Construction

| Nom | Description |
|-|-|
|[_com_ptr_t](../cpp/com-ptr-t-com-ptr-t.md)|Construit un objet **_com_ptr_t** .|

### <a name="low-level-operations"></a>Opérations de bas niveau

| Nom | Description |
|-|-|
|[AddRef](../cpp/com-ptr-t-addref.md)|Appelle la `AddRef` fonction membre de `IUnknown` sur le pointeur d’interface encapsulé.|
|[Attacher](../cpp/com-ptr-t-attach.md)|Encapsule un pointeur d'interface brut du type de ce pointeur intelligent.|
|[CreateInstance](../cpp/com-ptr-t-createinstance.md)|Crée une nouvelle instance d’un objet en fonction d’un ou d’un `CLSID` `ProgID` .|
|[Détacher](../cpp/com-ptr-t-detach.md)|Extrait et retourne le pointeur d'interface encapsulé.|
|[GetActiveObject](../cpp/com-ptr-t-getactiveobject.md)|Attache à une instance existante d’un objet à partir d’un ou d’un `CLSID` `ProgID` .|
|[GetInterfacePtr](../cpp/com-ptr-t-getinterfaceptr.md)|Retourne le pointeur d'interface encapsulé.|
|[QueryInterface](../cpp/com-ptr-t-queryinterface.md)|Appelle la `QueryInterface` fonction membre de `IUnknown` sur le pointeur d’interface encapsulé.|
|[Version release](../cpp/com-ptr-t-release.md)|Appelle la `Release` fonction membre de `IUnknown` sur le pointeur d’interface encapsulé.|

### <a name="operators"></a>Opérateurs

| Nom | Description |
|-|-|
|[opérateur =](../cpp/com-ptr-t-operator-equal.md)|Assigne une nouvelle valeur à un objet **_com_ptr_t** existant.|
|[opérateurs = =, ! =, \<, > , \<=, >=](../cpp/com-ptr-t-relational-operators.md)|Comparent l'objet pointeur intelligent avec un autre pointeur intelligent, un pointeur d'interface brut ou NULL.|
|[Extracteurs](../cpp/com-ptr-t-extractors.md)|Récupérez le pointeur d'interface COM encapsulé.|

**FIN spécifique à Microsoft**

## <a name="requirements"></a>Configuration requise

**En-tête :**\<comip.h>

**Lib :** comsuppw. lib ou comsuppwd. lib (consultez [/Zc : Wchar_t (Wchar_t est un type natif)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) pour plus d’informations)

## <a name="see-also"></a>Voir aussi

[Classes de prise en charge COM du compilateur](../cpp/compiler-com-support-classes.md)
