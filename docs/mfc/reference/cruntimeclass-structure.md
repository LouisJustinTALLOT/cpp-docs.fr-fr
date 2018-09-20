---
title: CRuntimeClass, Structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CRuntimeClass
dev_langs:
- C++
helpviewer_keywords:
- CRuntimeClass structure [MFC]
- dynamic class information [MFC]
- runtime [MFC], class information
- run-time class [MFC], CRuntimeClass structure
ms.assetid: de62b6ef-90d4-420f-8c70-f58b36976a2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8bc788e646b0e8f788dd8db97d5bc43c3240441f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402484"
---
# <a name="cruntimeclass-structure"></a>CRuntimeClass, Structure

Chaque classe dérivée de `CObject` est associé un `CRuntimeClass` structure que vous pouvez utiliser pour obtenir des informations sur un objet ou de sa classe de base au moment de l’exécution.

## <a name="syntax"></a>Syntaxe

```
struct CRuntimeClass
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CRuntimeClass::CreateObject](#createobject)|Crée un objet pendant l’exécution.|
|[CRuntimeClass::FromName](#fromname)|Crée un objet pendant l’exécution en utilisant le nom de classe familiers.|
|[CRuntimeClass::IsDerivedFrom](#isderivedfrom)|Détermine si la classe est dérivée de la classe spécifiée.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CRuntimeClass::m_lpszClassName](#m_lpszclassname)|Nom de la classe.|
|[CRuntimeClass::m_nObjectSize](#m_nobjectsize)|Taille de l'objet en octets.|
|[CRuntimeClass::m_pBaseClass](#m_pbaseclass)|Un pointeur vers le `CRuntimeClass` structure de la classe de base.|
|[CRuntimeClass::m_pfnCreateObject](#m_pfncreateobject)|Pointeur vers la fonction qui crée dynamiquement l’objet.|
|[CRuntimeClass::m_pfnGetBaseClass](#m_pfngetbaseclass)|Retourne le `CRuntimeClass` structure (uniquement disponible quand dynamiquement lié).|
|[CRuntimeClass::m_wSchema](#m_wschema)|Le numéro de schéma de la classe.|

## <a name="remarks"></a>Notes

`CRuntimeClass` est une structure et n’a donc pas une classe de base.

La possibilité de déterminer la classe d’un objet au moment de l’exécution est utile lors de la vérification des arguments de fonction de type supplémentaire est nécessaire, ou lorsque vous devez écrire un code spécial en fonction de la classe d’un objet. Les informations sur la classe d'exécution ne sont pas prises en charge directement par le langage C++.

`CRuntimeClass` Fournit des informations sur l’objet connexe de C++, comme un pointeur vers le `CRuntimeClass` de la classe de base et le nom de classe ASCII de la classe connexe. Cette structure implémente également les diverses fonctions qui peuvent être utilisées pour créer dynamiquement des objets, en spécifiant le type d’objet en utilisant un nom familier et déterminer si la classe associée est dérivée d’une classe spécifique.

Pour plus d’informations sur l’utilisation de `CRuntimeClass`, consultez l’article [l’accès aux informations sur la classe runtime](../../mfc/accessing-run-time-class-information.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CRuntimeClass`

## <a name="requirements"></a>Configuration requise

**En-tête :** afx.h

##  <a name="createobject"></a>  CRuntimeClass::CreateObject

Appelez cette fonction pour créer la classe spécifiée de manière dynamique pendant l’exécution.

```
CObject* CreateObject();

static CObject* PASCAL CreateObject(LPCSTR lpszClassName);

static CObject* PASCAL CreateObject(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>Paramètres

*lpszClassName*<br/>
Le nom familier de la classe à créer.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers l’objet nouvellement créé, ou NULL si le nom de classe est introuvable ou la mémoire est insuffisante pour créer l’objet.

### <a name="remarks"></a>Notes

Les classes dérivées de `CObject` peut de prendre en charge la création dynamique, ce qui est la possibilité de créer un objet d’une classe spécifiée au moment de l’exécution. Classes de document, vue et image, par exemple, doivent prendre en charge la création dynamique. Pour plus d’informations sur la création dynamique et le `CreateObject` membre, consultez [CObject, classe](../../mfc/using-cobject.md) et [classe CObject : en spécifiant les niveaux de fonctionnalité](../../mfc/specifying-levels-of-functionality.md).

### <a name="example"></a>Exemple

  Consultez l’exemple de [IsDerivedFrom](#isderivedfrom).

##  <a name="fromname"></a>  CRuntimeClass::FromName

Appelez cette fonction pour récupérer le `CRuntimeClass` structure associée au nom familier.

```
static CRuntimeClass* PASCAL FromName(LPCSTR lpszClassName);

static CRuntimeClass* PASCAL FromName(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>Paramètres

*lpszClassName*<br/>
Le nom familier d’une classe dérivée de `CObject`.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers un `CRuntimeClass` objet, correspondant au nom en tant que réussite dans *lpszClassName*. La fonction retourne NULL si aucun nom de classe correspondant a été trouvé.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCObjectSample#17](../../mfc/codesnippet/cpp/cruntimeclass-structure_1.cpp)]

##  <a name="isderivedfrom"></a>  CRuntimeClass::IsDerivedFrom

Appelez cette fonction pour déterminer si la classe appelante est dérivée de la classe spécifiée dans le *pBaseClass* paramètre.

```
BOOL IsDerivedFrom(const CRuntimeClass* pBaseClass) const;


```

### <a name="parameters"></a>Paramètres

*pBaseClass*<br/>
Le nom familier d’une classe dérivée de `CObject`.

### <a name="return-value"></a>Valeur de retour

TRUE si l’appel de la classe `IsDerivedFrom` est dérivée de la base de la classe dont `CRuntimeClass` structure est donnée en tant que paramètre ; sinon, FALSE.

### <a name="remarks"></a>Notes

La relation est déterminée par le « parcours » à partir de la classe du membre de la chaîne de classes dérivées jusqu’en haut. Cette fonction retourne uniquement la valeur FALSE si aucune correspondance n’est trouvée pour la classe de base.

> [!NOTE]
>  Pour utiliser le `CRuntimeClass` structure, vous devez inclure la macro IMPLEMENT_DYNAMIC, IMPLEMENT_DYNCREATE ou IMPLEMENT_SERIAL dans l’implémentation de la classe pour laquelle vous souhaitez récupérer les informations relatives aux objets d’exécution.

Pour plus d’informations sur l’utilisation de `CRuntimeClass`, consultez l’article [classe CObject : l’accès aux informations sur la classe runtime](../../mfc/accessing-run-time-class-information.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCObjectSample#18](../../mfc/codesnippet/cpp/cruntimeclass-structure_2.cpp)]

##  <a name="m_lpszclassname"></a>  CRuntimeClass::m_lpszClassName

Chaîne se terminant par null qui contient le nom de classe ASCII.

### <a name="remarks"></a>Notes

Ce nom peut être utilisé pour créer une instance de la classe à l’aide du `FromName` fonction membre.

### <a name="example"></a>Exemple

  Consultez l’exemple de [IsDerivedFrom](#isderivedfrom).

##  <a name="m_nobjectsize"></a>  CRuntimeClass::m_nObjectSize

La taille de l’objet, en octets.

### <a name="remarks"></a>Notes

Si l’objet a des membres de données qui pointent vers la mémoire allouée, la taille de cette mémoire n’est pas incluse.

### <a name="example"></a>Exemple

  Consultez l’exemple de [IsDerivedFrom](#isderivedfrom).

##  <a name="m_pbaseclass"></a>  CRuntimeClass::m_pBaseClass

Si votre application liée statiquement à MFC, ce membre de données contient un pointeur vers le `CRuntimeClass` structure de la classe de base.

### <a name="remarks"></a>Notes

Si votre application liée de manière dynamique à la bibliothèque MFC, consultez [m_pfnGetBaseClass](#m_pfngetbaseclass).

### <a name="example"></a>Exemple

  Consultez l’exemple de [IsDerivedFrom](#isderivedfrom).

##  <a name="m_pfncreateobject"></a>  CRuntimeClass::m_pfnCreateObject

Un pointeur de fonction au constructeur par défaut qui crée un objet de votre classe.

### <a name="remarks"></a>Notes

Ce pointeur est valide uniquement si la classe prend en charge la création dynamique ; Sinon, la fonction retourne NULL.

##  <a name="m_pfngetbaseclass"></a>  CRuntimeClass::m_pfnGetBaseClass

Si votre application utilise la bibliothèque MFC comme une DLL partagée, ce membre de données pointe vers une fonction qui retourne le `CRuntimeClass` structure de la classe de base.

### <a name="remarks"></a>Notes

Si votre application liée statiquement à la bibliothèque MFC, consultez [m_pBaseClass](#m_pbaseclass).

### <a name="example"></a>Exemple

  Consultez l’exemple de [IsDerivedFrom](#isderivedfrom).

##  <a name="m_wschema"></a>  CRuntimeClass::m_wSchema

Le numéro de schéma (-1 pour les classes non sérialisable).

### <a name="remarks"></a>Notes

Pour plus d’informations sur les numéros de schéma, consultez le [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) macro.

### <a name="example"></a>Exemple

  Consultez l’exemple de [IsDerivedFrom](#isderivedfrom).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CObject::GetRuntimeClass](../../mfc/reference/cobject-class.md#getruntimeclass)<br/>
[CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof)<br/>
[RUNTIME_CLASS](run-time-object-model-services.md#runtime_class)<br/>
[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)<br/>
[IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)<br/>
[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)



