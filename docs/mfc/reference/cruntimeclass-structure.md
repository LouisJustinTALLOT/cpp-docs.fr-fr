---
title: Structure CRuntimeClass
ms.date: 11/04/2016
f1_keywords:
- CRuntimeClass
helpviewer_keywords:
- CRuntimeClass structure [MFC]
- dynamic class information [MFC]
- runtime [MFC], class information
- run-time class [MFC], CRuntimeClass structure
ms.assetid: de62b6ef-90d4-420f-8c70-f58b36976a2b
ms.openlocfilehash: 92979a10c18d9759e0ecc9f0785e56a97c0f0642
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421442"
---
# <a name="cruntimeclass-structure"></a>Structure CRuntimeClass

Chaque classe dérivée de `CObject` est associée à une structure `CRuntimeClass` que vous pouvez utiliser pour obtenir des informations sur un objet ou sa classe de base au moment de l’exécution.

## <a name="syntax"></a>Syntaxe

```
struct CRuntimeClass
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CRuntimeClass :: CreateObject](#createobject)|Crée un objet au moment de l’exécution.|
|[CRuntimeClass :: FromName](#fromname)|Crée un objet au moment de l’exécution en utilisant le nom de classe familier.|
|[CRuntimeClass :: IsDerivedFrom](#isderivedfrom)|Détermine si la classe est dérivée de la classe spécifiée.|

### <a name="public-data-members"></a>Membres de données publics

|Name|Description|
|----------|-----------------|
|[CRuntimeClass :: m_lpszClassName](#m_lpszclassname)|Nom de la classe.|
|[CRuntimeClass :: m_nObjectSize](#m_nobjectsize)|Taille de l'objet en octets.|
|[CRuntimeClass :: m_pBaseClass](#m_pbaseclass)|Pointeur vers la structure `CRuntimeClass` de la classe de base.|
|[CRuntimeClass :: m_pfnCreateObject](#m_pfncreateobject)|Pointeur vers la fonction qui crée dynamiquement l’objet.|
|[CRuntimeClass :: m_pfnGetBaseClass](#m_pfngetbaseclass)|Retourne la structure `CRuntimeClass` (disponible uniquement en cas de liaison dynamique).|
|[CRuntimeClass :: m_wSchema](#m_wschema)|Numéro de schéma de la classe.|

## <a name="remarks"></a>Notes

`CRuntimeClass` est une structure et, par conséquent, n’a pas de classe de base.

La possibilité de déterminer la classe d’un objet au moment de l’exécution est utile quand une vérification de type supplémentaire des arguments de fonction est nécessaire ou lorsque vous devez écrire un code spécial basé sur la classe d’un objet. Les informations sur la classe d'exécution ne sont pas prises en charge directement par le langage C++.

`CRuntimeClass` fournit des informations sur l' C++ objet connexe, comme un pointeur vers le `CRuntimeClass` de la classe de base et le nom de la classe ASCII de la classe connexe. Cette structure implémente également diverses fonctions qui peuvent être utilisées pour créer dynamiquement des objets, en spécifiant le type d’objet à l’aide d’un nom familier et en déterminant si la classe associée est dérivée d’une classe spécifique.

Pour plus d’informations sur l’utilisation de `CRuntimeClass`, consultez l’article [accès aux informations de classe d’exécution](../../mfc/accessing-run-time-class-information.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

`CRuntimeClass`

## <a name="requirements"></a>Spécifications

**En-tête :** afx.h

##  <a name="createobject"></a>CRuntimeClass :: CreateObject

Appelez cette fonction pour créer dynamiquement la classe spécifiée au moment de l’exécution.

```
CObject* CreateObject();

static CObject* PASCAL CreateObject(LPCSTR lpszClassName);

static CObject* PASCAL CreateObject(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>Paramètres

*lpszClassName*<br/>
Nom familier de la classe à créer.

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’objet nouvellement créé, ou NULL si le nom de la classe est introuvable ou si la mémoire est insuffisante pour créer l’objet.

### <a name="remarks"></a>Notes

Les classes dérivées de `CObject` peuvent prendre en charge la création dynamique, qui est la possibilité de créer un objet d’une classe spécifiée au moment de l’exécution. Les classes document, vue et Frame, par exemple, doivent prendre en charge la création dynamique. Pour plus d’informations sur la création dynamique et le membre `CreateObject`, consultez [CObject, classe](../../mfc/using-cobject.md) et [classe CObject : spécification des niveaux de fonctionnalité](../../mfc/specifying-levels-of-functionality.md).

### <a name="example"></a>Exemple

  Consultez l’exemple pour [IsDerivedFrom](#isderivedfrom).

##  <a name="fromname"></a>CRuntimeClass :: FromName

Appelez cette fonction pour récupérer la structure `CRuntimeClass` associée au nom familier.

```
static CRuntimeClass* PASCAL FromName(LPCSTR lpszClassName);

static CRuntimeClass* PASCAL FromName(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>Paramètres

*lpszClassName*<br/>
Nom familier d’une classe dérivée de `CObject`.

### <a name="return-value"></a>Valeur de retour

Pointeur vers un objet `CRuntimeClass`, correspondant au nom passé dans *lpszClassName*. La fonction retourne la valeur NULL si aucun nom de classe correspondant n’a été trouvé.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCObjectSample#17](../../mfc/codesnippet/cpp/cruntimeclass-structure_1.cpp)]

##  <a name="isderivedfrom"></a>CRuntimeClass :: IsDerivedFrom

Appelez cette fonction pour déterminer si la classe appelante est dérivée de la classe spécifiée dans le paramètre *pBaseClass* .

```
BOOL IsDerivedFrom(const CRuntimeClass* pBaseClass) const;
```

### <a name="parameters"></a>Paramètres

*pBaseClass*<br/>
Nom familier d’une classe dérivée de `CObject`.

### <a name="return-value"></a>Valeur de retour

TRUE si la classe qui appelle `IsDerivedFrom` est dérivée de la classe de base dont la structure `CRuntimeClass` est fournie en tant que paramètre ; Sinon, FALSe.

### <a name="remarks"></a>Notes

La relation est déterminée en « progressant » de la classe du membre vers le haut de la chaîne des classes dérivées jusqu’en haut. Cette fonction retourne uniquement la valeur FALSe si aucune correspondance n’est trouvée pour la classe de base.

> [!NOTE]
>  Pour utiliser la structure `CRuntimeClass`, vous devez inclure la macro IMPLEMENT_DYNAMIC, IMPLEMENT_DYNCREATE ou IMPLEMENT_SERIAL dans l’implémentation de la classe pour laquelle vous souhaitez récupérer des informations relatives aux objets au moment de l’exécution.

Pour plus d’informations sur l’utilisation de `CRuntimeClass`, consultez l’article [CObject, classe : accès aux informations de classe d’exécution](../../mfc/accessing-run-time-class-information.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCObjectSample#18](../../mfc/codesnippet/cpp/cruntimeclass-structure_2.cpp)]

##  <a name="m_lpszclassname"></a>CRuntimeClass :: m_lpszClassName

Chaîne terminée par le caractère null qui contient le nom de la classe ASCII.

### <a name="remarks"></a>Notes

Ce nom peut être utilisé pour créer une instance de la classe à l’aide de la fonction membre `FromName`.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [IsDerivedFrom](#isderivedfrom).

##  <a name="m_nobjectsize"></a>CRuntimeClass :: m_nObjectSize

Taille de l’objet, en octets.

### <a name="remarks"></a>Notes

Si l’objet a des membres de données qui pointent vers la mémoire allouée, la taille de cette mémoire n’est pas incluse.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [IsDerivedFrom](#isderivedfrom).

##  <a name="m_pbaseclass"></a>CRuntimeClass :: m_pBaseClass

Si votre application est liée de manière statique aux MFC, ce membre de données contient un pointeur vers la structure `CRuntimeClass` de la classe de base.

### <a name="remarks"></a>Notes

Si votre application est liée de manière dynamique à la bibliothèque MFC, consultez [m_pfnGetBaseClass](#m_pfngetbaseclass).

### <a name="example"></a>Exemple

  Consultez l’exemple pour [IsDerivedFrom](#isderivedfrom).

##  <a name="m_pfncreateobject"></a>CRuntimeClass :: m_pfnCreateObject

Pointeur de fonction vers le constructeur par défaut qui crée un objet de votre classe.

### <a name="remarks"></a>Notes

Ce pointeur est valide uniquement si la classe prend en charge la création dynamique ; dans le cas contraire, la fonction retourne la valeur NULL.

##  <a name="m_pfngetbaseclass"></a>CRuntimeClass :: m_pfnGetBaseClass

Si votre application utilise la bibliothèque MFC comme DLL partagée, ce membre de données pointe vers une fonction qui retourne la structure `CRuntimeClass` de la classe de base.

### <a name="remarks"></a>Notes

Si votre application est liée statiquement à la bibliothèque MFC, consultez [m_pBaseClass](#m_pbaseclass).

### <a name="example"></a>Exemple

  Consultez l’exemple pour [IsDerivedFrom](#isderivedfrom).

##  <a name="m_wschema"></a>CRuntimeClass :: m_wSchema

Le numéro de schéma (-1 pour les classes non sérialisables).

### <a name="remarks"></a>Notes

Pour plus d’informations sur les numéros de schéma, consultez la macro [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) .

### <a name="example"></a>Exemple

  Consultez l’exemple pour [IsDerivedFrom](#isderivedfrom).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CObject :: GetRuntimeClass](../../mfc/reference/cobject-class.md#getruntimeclass)<br/>
[CObject :: IsKindOf](../../mfc/reference/cobject-class.md#iskindof)<br/>
[RUNTIME_CLASS](run-time-object-model-services.md#runtime_class)<br/>
[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)<br/>
[IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)<br/>
[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)
