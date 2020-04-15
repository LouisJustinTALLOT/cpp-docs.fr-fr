---
title: CRuntimeClass Structure
ms.date: 11/04/2016
f1_keywords:
- CRuntimeClass
helpviewer_keywords:
- CRuntimeClass structure [MFC]
- dynamic class information [MFC]
- runtime [MFC], class information
- run-time class [MFC], CRuntimeClass structure
ms.assetid: de62b6ef-90d4-420f-8c70-f58b36976a2b
ms.openlocfilehash: a58b9c97d5683423a0f81f6b5424f19f987943bf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318552"
---
# <a name="cruntimeclass-structure"></a>CRuntimeClass Structure

Chaque classe `CObject` dérivée est `CRuntimeClass` associée à une structure que vous pouvez utiliser pour obtenir des informations sur un objet ou sa classe de base au moment de l’exécution.

## <a name="syntax"></a>Syntaxe

```
struct CRuntimeClass
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CRuntimeClass::CréerObject](#createobject)|Crée un objet pendant le temps d’exécution.|
|[CRuntimeClass::DeName](#fromname)|Crée un objet pendant le temps d’exécution en utilisant le nom familier de classe.|
|[CRuntimeClass::IsDerivedDe](#isderivedfrom)|Détermine si la classe est dérivée de la classe spécifiée.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CRuntimeClass::m_lpszClassName](#m_lpszclassname)|Nom de la classe.|
|[CRuntimeClass::m_nObjectSize](#m_nobjectsize)|Taille de l'objet en octets.|
|[CRuntimeClass::m_pBaseClass](#m_pbaseclass)|Un pointeur `CRuntimeClass` à la structure de la classe de base.|
|[CRuntimeClass::m_pfnCreateObject](#m_pfncreateobject)|Un pointeur de la fonction qui crée dynamiquement l’objet.|
|[CRuntimeClass::m_pfnGetBaseClass](#m_pfngetbaseclass)|Retourne `CRuntimeClass` la structure (uniquement disponible lorsqu’elle est liée dynamiquement).|
|[CRuntimeClass::m_wSchema](#m_wschema)|Le numéro schéma de la classe.|

## <a name="remarks"></a>Notes

`CRuntimeClass`est une structure et n’a donc pas de classe de base.

La possibilité de déterminer la classe d’un objet au moment de l’exécution est utile lorsque la vérification type supplémentaire des arguments de fonction est nécessaire, ou lorsque vous devez écrire un code à usage spécial basé sur la classe d’un objet. Les informations sur la classe d'exécution ne sont pas prises en charge directement par le langage C++.

`CRuntimeClass`fournit des informations sur l’objet CMD connexe, comme un pointeur à la `CRuntimeClass` classe de base et le nom de classe ASCII de la classe connexe. Cette structure implémente également diverses fonctions qui peuvent être utilisées pour créer dynamiquement des objets, en spécifiant le type d’objet en utilisant un nom familier, et en déterminant si la classe connexe est dérivée d’une classe spécifique.

Pour plus d’informations sur l’utilisation `CRuntimeClass`, voir l’article [Accessing Run-Time Class Information](../../mfc/accessing-run-time-class-information.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CRuntimeClass`

## <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="cruntimeclasscreateobject"></a><a name="createobject"></a>CRuntimeClass::CréerObject

Appelez cette fonction pour créer dynamiquement la classe spécifiée pendant le temps d’exécution.

```
CObject* CreateObject();

static CObject* PASCAL CreateObject(LPCSTR lpszClassName);

static CObject* PASCAL CreateObject(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>Paramètres

*lpszClassName (en)*<br/>
Le nom familier de la classe à créer.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers l’objet nouvellement créé, ou NULL si le nom de classe n’est pas trouvé ou s’il n’y a pas suffisamment de mémoire pour créer l’objet.

### <a name="remarks"></a>Notes

Les classes `CObject` dérivées peuvent soutenir la création dynamique, qui est la capacité de créer un objet d’une classe spécifiée au moment de l’exécution. Les classes de documents, de visionnement et de cadre, par exemple, devraient soutenir la création dynamique. Pour plus d’informations `CreateObject` sur la création dynamique et le membre, voir [classe CObject](../../mfc/using-cobject.md) et [Classe CObject: Spécifier les niveaux de fonctionnalité](../../mfc/specifying-levels-of-functionality.md).

### <a name="example"></a>Exemple

  Voir l’exemple pour [IsDerivedDe](#isderivedfrom).

## <a name="cruntimeclassfromname"></a><a name="fromname"></a>CRuntimeClass::DeName

Appelez cette fonction `CRuntimeClass` pour récupérer la structure associée au nom familier.

```
static CRuntimeClass* PASCAL FromName(LPCSTR lpszClassName);

static CRuntimeClass* PASCAL FromName(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>Paramètres

*lpszClassName (en)*<br/>
Le nom familier d’une classe dérivée de `CObject`.

### <a name="return-value"></a>Valeur de retour

Un pointeur `CRuntimeClass` à un objet, correspondant au nom tel qu’il est passé dans *lpszClassName*. La fonction renvoie NULL si aucun nom de classe correspondant n’a été trouvé.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCObjectSample#17](../../mfc/codesnippet/cpp/cruntimeclass-structure_1.cpp)]

## <a name="cruntimeclassisderivedfrom"></a><a name="isderivedfrom"></a>CRuntimeClass::IsDerivedDe

Appelez cette fonction pour déterminer si la classe d’appel est dérivée de la classe spécifiée dans le paramètre *pBaseClass.*

```
BOOL IsDerivedFrom(const CRuntimeClass* pBaseClass) const;
```

### <a name="parameters"></a>Paramètres

*pBaseClass (en)*<br/>
Le nom familier d’une classe dérivée de `CObject`.

### <a name="return-value"></a>Valeur de retour

VRAI si l’appel `IsDerivedFrom` de classe `CRuntimeClass` est dérivé de la classe de base dont la structure est donnée comme paramètre; autrement FALSE.

### <a name="remarks"></a>Notes

La relation est déterminée par «marcher» de la classe du membre jusqu’à la chaîne de classes dérivées tout le chemin vers le haut. Cette fonction ne renvoie FALSE que si aucune correspondance n’est trouvée pour la classe de base.

> [!NOTE]
> Pour utiliser `CRuntimeClass` la structure, vous devez inclure les IMPLEMENT_DYNAMIC, IMPLEMENT_DYNCREATE ou IMPLEMENT_SERIAL macro dans la mise en œuvre de la classe pour laquelle vous souhaitez récupérer les informations d’objet en temps de course.

Pour plus d’informations sur l’utilisation `CRuntimeClass`, voir l’article [CObject Class: Accessing Run-Time Class Information](../../mfc/accessing-run-time-class-information.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCObjectSample#18](../../mfc/codesnippet/cpp/cruntimeclass-structure_2.cpp)]

## <a name="cruntimeclassm_lpszclassname"></a><a name="m_lpszclassname"></a>CRuntimeClass::m_lpszClassName

Une chaîne à durée nulle contenant le nom de classe ASCII.

### <a name="remarks"></a>Notes

Ce nom peut être utilisé pour créer `FromName` une instance de la classe en utilisant la fonction membre.

### <a name="example"></a>Exemple

  Voir l’exemple pour [IsDerivedDe](#isderivedfrom).

## <a name="cruntimeclassm_nobjectsize"></a><a name="m_nobjectsize"></a>CRuntimeClass::m_nObjectSize

La taille de l’objet, dans les octets.

### <a name="remarks"></a>Notes

Si l’objet a des membres de données qui pointent vers la mémoire allouée, la taille de cette mémoire n’est pas incluse.

### <a name="example"></a>Exemple

  Voir l’exemple pour [IsDerivedDe](#isderivedfrom).

## <a name="cruntimeclassm_pbaseclass"></a><a name="m_pbaseclass"></a>CRuntimeClass::m_pBaseClass

Si votre application est statiquement liée à MFC, `CRuntimeClass` ce membre des données contient un pointeur sur la structure de la classe de base.

### <a name="remarks"></a>Notes

Si votre application est reliée dynamiquement à la bibliothèque MFC, voir [m_pfnGetBaseClass](#m_pfngetbaseclass).

### <a name="example"></a>Exemple

  Voir l’exemple pour [IsDerivedDe](#isderivedfrom).

## <a name="cruntimeclassm_pfncreateobject"></a><a name="m_pfncreateobject"></a>CRuntimeClass::m_pfnCreateObject

Un pointeur de fonction pour le constructeur par défaut qui crée un objet de votre classe.

### <a name="remarks"></a>Notes

Ce pointeur n’est valable que si la classe prend en charge la création dynamique; autrement, la fonction renvoie NULL.

## <a name="cruntimeclassm_pfngetbaseclass"></a><a name="m_pfngetbaseclass"></a>CRuntimeClass::m_pfnGetBaseClass

Si votre application utilise la bibliothèque MFC comme DLL partagée, ce `CRuntimeClass` membre des données indique une fonction qui renvoie la structure de la classe de base.

### <a name="remarks"></a>Notes

Si votre application est reliée statiquement à la bibliothèque MFC, voir [m_pBaseClass](#m_pbaseclass).

### <a name="example"></a>Exemple

  Voir l’exemple pour [IsDerivedDe](#isderivedfrom).

## <a name="cruntimeclassm_wschema"></a><a name="m_wschema"></a>CRuntimeClass::m_wSchema

Le numéro de schéma (-1 pour les classes non-étialisables).

### <a name="remarks"></a>Notes

Pour plus d’informations sur les numéros de schéma, voir le [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) macro.

### <a name="example"></a>Exemple

  Voir l’exemple pour [IsDerivedDe](#isderivedfrom).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CObject::GetRuntimeClass](../../mfc/reference/cobject-class.md#getruntimeclass)<br/>
[CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof)<br/>
[RUNTIME_CLASS](run-time-object-model-services.md#runtime_class)<br/>
[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)<br/>
[IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)<br/>
[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)
