---
description: 'En savoir plus sur : classe CObject'
title: CObject (classe)
ms.date: 1/12/2021
f1_keywords:
- CObject
- AFX/CObject
- AFX/CObject::CObject
- AFX/CObject::AssertValid
- AFX/CObject::Dump
- AFX/CObject::GetRuntimeClass
- AFX/CObject::IsKindOf
- AFX/CObject::IsSerializable
- AFX/CObject::Serialize
helpviewer_keywords:
- CObject [MFC], CObject
- CObject [MFC], AssertValid
- CObject [MFC], Dump
- CObject [MFC], GetRuntimeClass
- CObject [MFC], IsKindOf
- CObject [MFC], IsSerializable
- CObject [MFC], Serialize
ms.openlocfilehash: ba152a9cbbe6e2fa217d6c2e24d13ea48dd37c87
ms.sourcegitcommit: b51f79b5394e12cd90cb65c85cc01716f90bfc90
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98167006"
---
# <a name="cobject-class"></a>La classe `CObject`

Classe de base principale pour la bibliothèque MFC (Microsoft Foundation Class).

## <a name="syntax"></a>Syntaxe

```cpp
class AFX_NOVTABLE CObject
```

## <a name="members"></a>Membres

### <a name="protected-constructors"></a>Constructeurs protégés

|Name|Description|
|----------|-----------------|
|[`CObject::CObject`](#cobject)|Constructeur par défaut.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[`CObject::AssertValid`](#assertvalid)|Valide l’intégrité de cet objet.|
|[`CObject::Dump`](#dump)|Produit un vidage des diagnostics de cet objet.|
|[`CObject::GetRuntimeClass`](#getruntimeclass)|Retourne la `CRuntimeClass` structure correspondant à la classe de cet objet.|
|[`CObject::IsKindOf`](#iskindof)|Teste la relation de cet objet avec une classe donnée.|
|[`CObject::IsSerializable`](#isserializable)|Teste si cet objet peut être sérialisé.|
|[`CObject::Serialize`](#serialize)|Charge ou stocke un objet à partir d’une archive.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Name|Description|
|----------|-----------------|
|[`CObject::operator delete`](#operator_delete)|**`delete`** Opérateur spécial.|
|[`CObject::operator new`](#operator_new)|**`new`** Opérateur spécial.|

## <a name="remarks"></a>Notes

Il sert de racine non seulement pour les classes de bibliothèque telles que `CFile` et `CObList` , mais également pour les classes que vous écrivez. `CObject` fournit des services de base, notamment

- Prise en charge de la sérialisation
- Informations de classe au moment de l’exécution
- Sortie de diagnostic d’objet
- Compatibilité avec les classes de collection

`CObject` ne prend pas en charge l’héritage multiple. Vos classes dérivées ne peuvent avoir qu’une seule `CObject` classe de base, et `CObject` doivent être les plus à gauche dans la hiérarchie. Toutefois, il est possible d’avoir des structures et des `CObject` classes non dérivées dans des branches à héritage multiple à droite.

Vous bénéficierez des principaux avantages de `CObject` la dérivation si vous utilisez certaines macros facultatives dans votre implémentation de classe et vos déclarations.

Les macros de premier niveau, [`DECLARE_DYNAMIC`](run-time-object-model-services.md#declare_dynamic) et [`IMPLEMENT_DYNAMIC`](run-time-object-model-services.md#implement_dynamic) , autorisent l’accès au moment de l’exécution au nom de la classe et à sa position dans la hiérarchie. Cela permet, à son tour, un vidage du diagnostic significatif.

Les macros de second niveau, [`DECLARE_SERIAL`](run-time-object-model-services.md#declare_serial) et [`IMPLEMENT_SERIAL`](run-time-object-model-services.md#implement_serial) , incluent toutes les fonctionnalités des macros de premier niveau, et elles permettent à un objet d’être « sérialisé » vers et à partir d’une « archive ».

Pour plus d’informations sur la dérivation des classes Microsoft Foundation et des classes C++ en général et l’utilisation de `CObject` , consultez [utilisation de CObject](../../mfc/using-cobject.md) et [sérialisation](../../mfc/serialization-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CObject`

## <a name="requirements"></a>Configuration requise

**En-tête :**`afx.h`

## <a name="cobjectassertvalid"></a><a name="assertvalid"></a> CObject :: AssertValid

Valide l’intégrité de cet objet.

```cpp
virtual void AssertValid() const;
```

### <a name="remarks"></a>Notes

`AssertValid` effectue une vérification de validité sur cet objet en vérifiant son état interne. Dans la version Debug de la bibliothèque, `AssertValid` peut déclarer, puis terminer le programme avec un message qui indique le numéro de ligne et le nom de fichier où l’assertion a échoué.

Lorsque vous écrivez votre propre classe, vous devez substituer la `AssertValid` fonction pour fournir des services de diagnostic pour vous et d’autres utilisateurs de votre classe. Le substitué `AssertValid` appelle généralement la `AssertValid` fonction de sa classe de base avant de vérifier les membres de données uniques à la classe dérivée.

Étant donné que `AssertValid` est une **`const`** fonction, vous n’êtes pas autorisé à modifier l’état de l’objet pendant le test. Vos propres fonctions de classe dérivée `AssertValid` ne doivent pas lever d’exceptions mais doivent plutôt déclarer si elles détectent des données d’objet non valides.

La définition de « validité » dépend de la classe de l’objet. En règle générale, la fonction doit effectuer une « vérification superficielle ». Autrement dit, si un objet contient des pointeurs vers d’autres objets, il doit vérifier si les pointeurs ne sont pas `NULL` , mais il ne doit pas effectuer de test de validité sur les objets référencés par les pointeurs.

### <a name="example"></a>Exemple

[`CObList::CObList`](../../mfc/reference/coblist-class.md#coblist)Pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples, consultez `CObject` .

[!code-cpp[NVC_MFCCObjectSample#7](../../mfc/codesnippet/cpp/cobject-class_1.cpp)]

Pour obtenir un autre exemple, consultez [`AfxDoForAllObjects`](diagnostic-services.md#afxdoforallobjects) .

## <a name="cobjectcobject"></a><a name="cobject"></a> CObject :: CObject

Ces fonctions sont les `CObject` constructeurs standard.

```cpp
CObject();
CObject(const CObject& objectSrc);
```

### <a name="parameters"></a>Paramètres

*objectSrc*\
Une référence à une autre `CObject`

### <a name="remarks"></a>Notes

La version par défaut est appelée automatiquement par le constructeur de votre classe dérivée.

Si votre classe est sérialisable (elle incorpore la `IMPLEMENT_SERIAL` macro), vous devez avoir un constructeur par défaut (un constructeur sans arguments) dans votre déclaration de classe. Si vous n’avez pas besoin d’un constructeur par défaut, déclarez un constructeur « vide » privé ou protégé. Pour plus d’informations, [consultez `CObject` utilisation ](../../mfc/using-cobject.md)de.

Le constructeur de copie de classe par défaut C++ standard effectue une copie de membre par membre. La présence du constructeur de `CObject` copie privé garantit un message d’erreur du compilateur si le constructeur de copie de votre classe est nécessaire, mais n’est pas disponible. Fournissez un constructeur de copie si votre classe requiert cette fonctionnalité.

### <a name="example"></a>Exemple

Pour obtenir la [`CObList::CObList`](../../mfc/reference/coblist-class.md#coblist) liste de la `CAge` classe utilisée dans les `CObject` exemples, consultez.

[!code-cpp[NVC_MFCCObjectSample#8](../../mfc/codesnippet/cpp/cobject-class_2.cpp)]

## <a name="cobjectdump"></a><a name="dump"></a> CObject ::D UMP

Vide le contenu de votre objet dans un [`CDumpContext`](../../mfc/reference/cdumpcontext-class.md) objet.

```cpp
virtual void Dump(CDumpContext& dc) const;
```

### <a name="parameters"></a>Paramètres

*métafichier*\
Le contexte de vidage du diagnostic pour le vidage, généralement `afxDump` .

### <a name="remarks"></a>Notes

Lorsque vous écrivez votre propre classe, vous devez substituer la `Dump` fonction pour fournir des services de diagnostic pour vous et d’autres utilisateurs de votre classe. Le substitué `Dump` appelle généralement la `Dump` fonction de sa classe de base avant d’imprimer des membres de données uniques à la classe dérivée. `CObject::Dump` imprime le nom de la classe si votre classe utilise la `IMPLEMENT_DYNAMIC` `IMPLEMENT_SERIAL` macro ou.

> [!NOTE]
> Votre `Dump` fonction ne doit pas imprimer un caractère de saut de ligne à la fin de sa sortie.

`Dump` les appels ont un sens uniquement dans la version de débogage du bibliothèque MFC (Microsoft Foundation Class). Vous devez mettre entre crochets les appels, les déclarations de fonction et les implémentations de fonctions avec des `#ifdef _DEBUG` `#endif` instructions pour la compilation conditionnelle.

Étant donné que `Dump` est une **`const`** fonction, vous n’êtes pas autorisé à modifier l’état de l’objet pendant le vidage.

L' [ `CDumpContext` opérateur d’insertion (<<)](../../mfc/reference/cdumpcontext-class.md#operator_lt_lt) appelle `Dump` lorsqu’un `CObject` pointeur est inséré.

`Dump` autorise uniquement le vidage « acycliques » des objets. Vous pouvez faire un dump d’une liste d’objets, par exemple, mais si l’un des objets est la liste elle-même, vous finira par déborder la pile.

### <a name="example"></a>Exemple

[`CObList::CObList`](../../mfc/reference/coblist-class.md#coblist)Pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples, consultez `CObject` .

[!code-cpp[NVC_MFCCObjectSample#9](../../mfc/codesnippet/cpp/cobject-class_3.cpp)]

## <a name="cobjectgetruntimeclass"></a><a name="getruntimeclass"></a> CObject :: GetRuntimeClass

Retourne la `CRuntimeClass` structure correspondant à la classe de cet objet.

```cpp
virtual CRuntimeClass* GetRuntimeClass() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers la [`CRuntimeClass`](../../mfc/reference/cruntimeclass-structure.md) structure qui correspond à la classe de cet objet ; jamais **`NULL`** .

### <a name="remarks"></a>Notes

Il existe une `CRuntimeClass` structure pour chaque `CObject` classe dérivée de. Les membres de la structure sont les suivants :

- **`LPCSTR m_lpszClassName`** Chaîne terminée par le caractère null qui contient le nom de la classe ASCII.
- **`int m_nObjectSize`** Taille de l’objet, en octets. Si l’objet a des membres de données qui pointent vers la mémoire allouée, la taille de cette mémoire n’est pas incluse.
- **`UINT m_wSchema`** Le numéro de schéma (-1 pour les classes non sérialisables). Consultez la [`IMPLEMENT_SERIAL`](run-time-object-model-services.md#implement_serial) macro pour obtenir une description du numéro de schéma.

- **`CObject* (PASCAL* m_pfnCreateObject)()`** Pointeur de fonction vers le constructeur par défaut qui crée un objet de votre classe (valide uniquement si la classe prend en charge la création dynamique ; sinon, retourne **`NULL`** ).

- **`CRuntimeClass* (PASCAL* m_pfn_GetBaseClass )()`** Si votre application est liée de manière dynamique à la version AFXDLL de MFC, pointeur vers une fonction qui retourne la `CRuntimeClass` structure de la classe de base.

- **`CRuntimeClass* m_pBaseClass`** Si votre application est liée de manière statique aux MFC, il s’agit d’un pointeur vers la `CRuntimeClass` structure de la classe de base.

Cette fonction requiert l’utilisation de [`IMPLEMENT_DYNAMIC`](run-time-object-model-services.md#implement_dynamic) la [`IMPLEMENT_DYNCREATE`](run-time-object-model-services.md#implement_dyncreate) macro, ou [`IMPLEMENT_SERIAL`](run-time-object-model-services.md#implement_serial) dans l’implémentation de classe. Dans le cas contraire, vous obtiendrez des résultats incorrects.

### <a name="example"></a>Exemple

[`CObList::CObList`](../../mfc/reference/coblist-class.md#coblist)Pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples, consultez `CObject` .

[!code-cpp[NVC_MFCCObjectSample#10](../../mfc/codesnippet/cpp/cobject-class_4.cpp)]

## <a name="cobjectiskindof"></a><a name="iskindof"></a> CObject :: IsKindOf

Teste la relation de cet objet avec une classe donnée.

```cpp
BOOL IsKindOf(const CRuntimeClass* pClass) const;
```

### <a name="parameters"></a>Paramètres

*`pClass`*\
Pointeur vers une [`CRuntimeClass`](../../mfc/reference/cruntimeclass-structure.md) structure associée à votre `CObject` classe dérivée de.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’objet correspond à la classe ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction teste *`pClass`* si (1) il s’agit d’un objet de la classe spécifiée ou (2) il s’agit d’un objet d’une classe dérivée de la classe spécifiée. Cette fonction ne fonctionne que pour les classes déclarées avec la [`DECLARE_DYNAMIC`](run-time-object-model-services.md#declare_dynamic) [`DECLARE_DYNCREATE`](run-time-object-model-services.md#declare_dyncreate) macro, ou [`DECLARE_SERIAL`](run-time-object-model-services.md#declare_serial) .

N’utilisez pas cette fonction de manière intensive, car elle est à l’encontre de la fonctionnalité de polymorphisme C++. Utilisez à la place des fonctions virtuelles.

### <a name="example"></a>Exemple

[`CObList::CObList`](../../mfc/reference/coblist-class.md#coblist)Pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples, consultez `CObject` .

[!code-cpp[NVC_MFCCObjectSample#11](../../mfc/codesnippet/cpp/cobject-class_5.cpp)]

## <a name="cobjectisserializable"></a><a name="isserializable"></a> CObject :: IsSerializable

Teste si cet objet est éligible pour la sérialisation.

```cpp
BOOL IsSerializable() const;
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si cet objet peut être sérialisé ; Sinon, 0.

### <a name="remarks"></a>Notes

Pour qu’une classe soit sérialisable, sa déclaration doit contenir la [`DECLARE_SERIAL`](run-time-object-model-services.md#declare_serial) macro, et l’implémentation doit contenir la [`IMPLEMENT_SERIAL`](run-time-object-model-services.md#implement_serial) macro.

> [!NOTE]
> Ne substituez pas cette fonction.

### <a name="example"></a>Exemple

[`CObList::CObList`](../../mfc/reference/coblist-class.md#coblist)Pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples, consultez `CObject` .

[!code-cpp[NVC_MFCCObjectSample#12](../../mfc/codesnippet/cpp/cobject-class_6.cpp)]

## <a name="cobjectoperator-delete"></a><a name="operator_delete"></a> CObject :: Operator supprimer

Pour la version Release de la bibliothèque, l’opérateur **`delete`** libère la mémoire allouée par l’opérateur **`new`** .

```cpp
void PASCAL operator delete(void* p);

void PASCAL operator delete(
    void* p,
    void* pPlace);

void PASCAL operator delete(
    void* p,
    LPCSTR lpszFileName,
    int nLine);
```

### <a name="remarks"></a>Notes

Dans la version de débogage, l’opérateur **`delete`** participe à un modèle de contrôle d’allocation conçu pour détecter les fuites de mémoire.

Si vous utilisez la ligne de code

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

avant l’une de vos implémentations dans un. CPP, la troisième version de **`delete`** sera utilisée, en stockant le nom de fichier et le numéro de ligne dans le bloc alloué pour les rapports ultérieurs. Vous n’avez pas à vous soucier de la fourniture des paramètres supplémentaires. une macro s’occupe de cela pour vous.

Même si vous n’utilisez pas `DEBUG_NEW` en mode débogage, vous bénéficiez toujours de la détection des fuites, mais sans le nombre de numéros de ligne du fichier source décrit ci-dessus.

Si vous remplacez les opérateurs **`new`** et **`delete`** , vous avez perdu cette fonctionnalité de diagnostic.

### <a name="example"></a>Exemple

Pour obtenir la [`CObList::CObList`](../../mfc/reference/coblist-class.md#coblist) liste de la `CAge` classe utilisée dans les `CObject` exemples, consultez.

[!code-cpp[NVC_MFCCObjectSample#15](../../mfc/codesnippet/cpp/cobject-class_8.cpp)]

## <a name="cobjectoperator-new"></a><a name="operator_new"></a> CObject :: operator new

Pour la version Release de la bibliothèque, l’opérateur **`new`** effectue une allocation de mémoire optimale de la même manière que `malloc` .

```cpp
void* PASCAL operator new(size_t nSize);
void* PASCAL operator new(size_t, void* p);

void* PASCAL operator new(
    size_t nSize,
    LPCSTR lpszFileName,
    int nLine);
```

### <a name="remarks"></a>Notes

Dans la version de débogage, l’opérateur **`new`** participe à un modèle de contrôle d’allocation conçu pour détecter les fuites de mémoire.

Si vous utilisez la ligne de code

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

avant l’une de vos implémentations dans un. CPP, la deuxième version de **`new`** sera utilisée, en stockant le nom de fichier et le numéro de ligne dans le bloc alloué pour les rapports ultérieurs. Vous n’avez pas à vous soucier de la fourniture des paramètres supplémentaires. une macro s’occupe de cela pour vous.

Même si vous n’utilisez pas `DEBUG_NEW` en mode débogage, vous bénéficiez toujours de la détection des fuites, mais sans le nombre de numéros de ligne du fichier source décrit ci-dessus.

> [!NOTE]
> Si vous remplacez cet opérateur, vous devez également substituer **`delete`** . N’utilisez pas la fonction de bibliothèque standard `_new_handler` .

### <a name="example"></a>Exemple

Pour obtenir la [`CObList::CObList`](../../mfc/reference/coblist-class.md#coblist) liste de la `CAge` classe utilisée dans les `CObject` exemples, consultez.

[!code-cpp[NVC_MFCCObjectSample#16](../../mfc/codesnippet/cpp/cobject-class_9.h)]

## <a name="cobjectserialize"></a><a name="serialize"></a> CObject :: Serialize

Lit ou écrit cet objet dans une archive.

```cpp
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Paramètres

*`ar`*\
`CArchive`Objet à sérialiser vers ou à partir de.

### <a name="remarks"></a>Notes

Substituez `Serialize` pour chaque classe que vous souhaitez sérialiser. Le substitué `Serialize` doit d’abord appeler la `Serialize` fonction de sa classe de base.

Vous devez également utiliser la [`DECLARE_SERIAL`](run-time-object-model-services.md#declare_serial) macro dans votre déclaration de classe, et vous devez utiliser la [`IMPLEMENT_SERIAL`](run-time-object-model-services.md#implement_serial) macro dans l’implémentation de.

Utilisez [`CArchive::IsLoading`](../../mfc/reference/carchive-class.md#isloading) ou [`CArchive::IsStoring`](../../mfc/reference/carchive-class.md#isstoring) pour déterminer si l’archive est en cours de chargement ou de stockage.

`Serialize` est appelé par [`CArchive::ReadObject`](../../mfc/reference/carchive-class.md#readobject) et [`CArchive::WriteObject`](../../mfc/reference/carchive-class.md#writeobject) . Ces fonctions sont associées à l' `CArchive` opérateur d’insertion ( **`<<`** ) et à l’opérateur d’extraction ( **`>>`** ).

Pour obtenir des exemples de sérialisation, consultez l’article [sérialisation d’un objet](../../mfc/serialization-serializing-an-object.md).

### <a name="example"></a>Exemple

[`CObList::CObList`](../../mfc/reference/coblist-class.md#coblist)Pour obtenir la liste de la `CAge` classe utilisée dans tous les exemples, consultez `CObject` .

[!code-cpp[NVC_MFCCObjectSample#13](../../mfc/codesnippet/cpp/cobject-class_10.cpp)]

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
