---
title: CObject (classe)
ms.date: 11/04/2016
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
ms.assetid: 95e9acd3-d9eb-4ac0-b52b-ca4a501a7a3a
ms.openlocfilehash: eb0580f6fef39df29d66e15cfd051a0460cb8d56
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584013"
---
# <a name="cobject-class"></a>CObject (classe)

Classe de base principale pour la bibliothèque MFC (Microsoft Foundation Class).

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE CObject
```

## <a name="members"></a>Membres

### <a name="protected-constructors"></a>Constructeurs protégés

|Nom|Description|
|----------|-----------------|
|[CObject::CObject](#cobject)|Constructeur par défaut.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CObject::AssertValid](#assertvalid)|Valide l’intégrité de cet objet.|
|[CObject::Dump](#dump)|Génère un vidage de diagnostic de cet objet.|
|[CObject::GetRuntimeClass](#getruntimeclass)|Retourne le `CRuntimeClass` structure correspondant à cette classe de l’objet.|
|[CObject::IsKindOf](#iskindof)|Teste la relation de cet objet à une classe donnée.|
|[CObject::IsSerializable](#isserializable)|Teste si cet objet peut être sérialisé.|
|[CObject::Serialize](#serialize)|Charge ou stocke un objet à partir / vers une archive.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[Suppression de CObject::operator](#operator_delete)|Spécial **supprimer** opérateur.|
|[CObject::operator nouveau](#operator_new)|Spécial **nouveau** opérateur.|

## <a name="remarks"></a>Notes

Il sert de racine non seulement pour les classes de bibliothèque comme `CFile` et `CObList`, mais également pour les classes que vous écrivez. `CObject` Fournit des services de base, y compris

- Prise en charge de la sérialisation

- Informations de classe d’exécution

- Sortie de diagnostic d’objet

- Compatibilité avec les classes de collection

Notez que `CObject` ne prend pas en charge l’héritage multiple. Vos classes dérivées peuvent avoir un seul `CObject` classe de base et `CObject` doit être plus à gauche dans la hiérarchie. Admissible, cependant, il est d’avoir des structures et non- `CObject`-classes dérivées de droite branches d’héritage multiple.

Vous constaterez des principaux avantages de `CObject` dérivation si vous utilisez certaines des macros facultatifs dans votre implémentation de la classe et les déclarations.

Les macros de premier niveau, [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic) et [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic), autoriser l’accès d’exécution pour le nom de classe et de sa position dans la hiérarchie. Cela, permet à son tour, vidage de diagnostic significatifs.

Les macros de second niveau, [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) et [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial), inclure toutes les fonctionnalités des macros de premier niveau, et ils permettent à un objet doit être « sérialisé » vers et à partir d’une « archive ».

Pour plus d’informations sur la dérivation de Microsoft Foundation classes et des classes C++ en général et à l’aide de `CObject`, consultez [à l’aide de CObject](../../mfc/using-cobject.md) et [sérialisation](../../mfc/serialization-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CObject`

## <a name="requirements"></a>Configuration requise

**En-tête :** afx.h

##  <a name="assertvalid"></a>  CObject::AssertValid

Valide l’intégrité de cet objet.

```
virtual void AssertValid() const;
```

### <a name="remarks"></a>Notes

`AssertValid` effectue une vérification de validité sur cet objet en vérifiant son état interne. Dans la version Debug de la bibliothèque, `AssertValid` peut déclarer et donc fin avec un message qui répertorie le numéro de ligne et le nom de fichier où l’assertion a échoué.

Quand vous écrivez votre propre classe, vous devez substituer la `AssertValid` fonction pour fournir des services de diagnostic pour vous-même et d’autres utilisateurs de votre classe. Substituées `AssertValid` appelle généralement la `AssertValid` fonction de sa classe de base avant de vérifier les membres de données uniques à la classe dérivée.

Étant donné que `AssertValid` est un **const** (fonction), vous n’êtes pas autorisé à modifier l’état de l’objet pendant le test. Votre propre classe dérivée `AssertValid` fonctions lever d’exceptions mais plutôt doit déclarer si ils détectent les données d’objet non valide.

La définition de « validité » dépend de la classe de l’objet. En règle générale, la fonction doit effectuer une « vérification superficielle ». Autrement dit, si un objet contient des pointeurs vers d’autres objets, il doit vérifier a posteriori si les pointeurs ne sont pas null, mais il ne doit pas exécuter des tests sur les objets référencés par les pointeurs de validité.

### <a name="example"></a>Exemple

Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les `CObject` exemples.

[!code-cpp[NVC_MFCCObjectSample#7](../../mfc/codesnippet/cpp/cobject-class_1.cpp)]

Pour un autre exemple, consultez [AfxDoForAllObjects](diagnostic-services.md#afxdoforallobjects).

##  <a name="cobject"></a>  CObject::CObject

Ces fonctions sont la norme `CObject` constructeurs.

```
CObject();
CObject(const CObject& objectSrc);
```

### <a name="parameters"></a>Paramètres

*objectSrc*<br/>
Une référence à un autre `CObject`

### <a name="remarks"></a>Notes

La version par défaut est automatiquement appelée par le constructeur de votre classe dérivée.

Si votre classe soit sérialisable (il incorpore la macro IMPLEMENT_SERIAL), vous devez disposer d’un constructeur par défaut (un constructeur sans arguments) dans votre déclaration de classe. Si vous n’avez pas besoin d’un constructeur par défaut, déclarez un privé ou protégé constructeur « vide ». Pour plus d’informations, consultez [à l’aide de CObject](../../mfc/using-cobject.md).

Le constructeur de copie de classe C++ par défaut standard effectue une copie de membre par membre. La présence de privé `CObject` constructeur de copie garantit un message d’erreur du compilateur si le constructeur de copie de votre classe est nécessaire mais non disponible. Vous devez donc fournir un constructeur de copie si votre classe requiert cette fonctionnalité.

### <a name="example"></a>Exemple

Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans le `CObject` exemples.

[!code-cpp[NVC_MFCCObjectSample#8](../../mfc/codesnippet/cpp/cobject-class_2.cpp)]

##  <a name="dump"></a>  CObject::Dump

Vide le contenu de votre objet à un [CDumpContext](../../mfc/reference/cdumpcontext-class.md) objet.

```
virtual void Dump(CDumpContext& dc) const;
```

### <a name="parameters"></a>Paramètres

*dc*<br/>
Le contexte de dump de diagnostic pour vider, généralement `afxDump`.

### <a name="remarks"></a>Notes

Quand vous écrivez votre propre classe, vous devez substituer la `Dump` fonction pour fournir des services de diagnostic pour vous-même et d’autres utilisateurs de votre classe. Substituées `Dump` appelle généralement la `Dump` fonction de sa classe de base avant d’imprimer des membres de données uniques à la classe dérivée. `CObject::Dump` Imprime le nom de classe si votre classe utilise le `IMPLEMENT_DYNAMIC` ou la macro IMPLEMENT_SERIAL.

> [!NOTE]
>  Votre `Dump` fonction ne doit pas afficher un caractère de saut de ligne à la fin de sa sortie.

`Dump` appels de sens que dans la version Debug de la bibliothèque Microsoft Foundation Class. Vous devez mettre entre parenthèses des appels, les déclarations de fonction et les implémentations de fonctions avec **#ifdef _DEBUG** /  `#endif` instructions pour la compilation conditionnelle.

Dans la mesure où `Dump` est un **const** (fonction), vous n’êtes pas autorisé à modifier l’état de l’objet pendant le vidage.

Le [CDumpContext insertion (<<) opérateur](../../mfc/reference/cdumpcontext-class.md#operator_lt_lt) appels `Dump` lorsqu’un `CObject` pointeur est inséré.

`Dump` autorise uniquement « acycliques » dump d’objets. Vous pouvez faire un dump une liste d’objets, par exemple, mais si l’un des objets est la liste elle-même, vous serez finalement dépassement de la pile.

### <a name="example"></a>Exemple

Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les `CObject` exemples.

[!code-cpp[NVC_MFCCObjectSample#9](../../mfc/codesnippet/cpp/cobject-class_3.cpp)]

##  <a name="getruntimeclass"></a>  CObject::GetRuntimeClass

Retourne le `CRuntimeClass` structure correspondant à cette classe de l’objet.

```
virtual CRuntimeClass* GetRuntimeClass() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) structure correspondant à cette classe de l’objet ; jamais **NULL**.

### <a name="remarks"></a>Notes

Il y a un `CRuntimeClass` structure pour chaque `CObject`-classe dérivée. Les membres de structure sont les suivantes :

- **LPCSTR m_lpszClassName** une chaîne se terminant par null qui contient le nom de classe ASCII.

- **int m_nObjectSize** la taille de l’objet, en octets. Si l’objet a des membres de données qui pointent vers la mémoire allouée, la taille de cette mémoire n’est pas incluse.

- **UINT m_wSchema** le numéro de schéma (-1 pour les classes non sérialisable). Consultez le [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) macro pour obtenir une description de numéro de schéma.

- **CObject\* (PASCAL\* m_pfnCreateObject) ()** un pointeur de fonction au constructeur par défaut qui crée un objet de votre classe (valide uniquement si la classe prend en charge la création dynamique ; sinon, retourne **NULL** ).

- **CRuntimeClass\* (PASCAL\* m_pfn_GetBaseClass) ()** si votre application est dynamiquement liée à la version d’AFXDLL de MFC, un pointeur vers une fonction qui retourne le `CRuntimeClass` structure de la classe de base.

- **CRuntimeClass\* m_pBaseClass** si votre application est liée de manière statique aux MFC, un pointeur vers le `CRuntimeClass` structure de la classe de base.

Cette fonction nécessite l’utilisation de la [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic), [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate), ou [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) macro dans l’implémentation de classe. Vous obtiendrez des résultats incorrects dans le cas contraire.

### <a name="example"></a>Exemple

Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les `CObject` exemples.

[!code-cpp[NVC_MFCCObjectSample#10](../../mfc/codesnippet/cpp/cobject-class_4.cpp)]

##  <a name="iskindof"></a>  CObject::IsKindOf

Teste la relation de cet objet à une classe donnée.

```
BOOL IsKindOf(const CRuntimeClass* pClass) const;
```

### <a name="parameters"></a>Paramètres

*pClass*<br/>
Un pointeur vers un [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) structure associée à votre `CObject`-classe dérivée.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’objet correspond à la classe ; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction teste *pClass* pour voir si (1) il est un objet de la classe spécifiée ou (2) il est un objet d’une classe dérivée de la classe spécifiée. Cette fonction fonctionne uniquement pour les classes déclarées avec le [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic), [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate), ou [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) macro.

N’utilisez pas cette fonction largement car elle occulte la fonctionnalité de polymorphisme C++. Utilisez plutôt les fonctions virtuelles.

### <a name="example"></a>Exemple

Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les `CObject` exemples.

[!code-cpp[NVC_MFCCObjectSample#11](../../mfc/codesnippet/cpp/cobject-class_5.cpp)]

##  <a name="isserializable"></a>  CObject::IsSerializable

Teste si cet objet est éligible pour la sérialisation.

```
BOOL IsSerializable() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si cet objet peut être sérialisé ; sinon 0.

### <a name="remarks"></a>Notes

Pour une classe soit sérialisable, sa déclaration doit contenir le [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) (macro) et l’implémentation doivent contenir le [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) macro.

> [!NOTE]
>  Ne remplacez pas cette fonction.

### <a name="example"></a>Exemple

Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les `CObject` exemples.

[!code-cpp[NVC_MFCCObjectSample#12](../../mfc/codesnippet/cpp/cobject-class_6.cpp)]

##  <a name="operator_delete"></a>  Suppression de CObject::operator

Pour la version de la bibliothèque, opérateur **supprimer** libère la mémoire allouée par opérateur **nouveau**.

```
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

Dans la version Debug, opérateur **supprimer** participe à un schéma d’allocation de la surveillance conçu pour détecter les fuites de mémoire.

Si vous utilisez la ligne de code

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

avant tout vos implémentations d’un. CPP de fichiers, puis la troisième version de **supprimer** doit être utilisé, en stockant le nom de fichier et numéro de ligne dans le bloc alloué pour générer un rapport ultérieur. Vous n’avez pas à vous soucier d’en fournissant les paramètres supplémentaires ; une macro s’occupe de cela pour vous.

Même si vous n’utilisez pas DEBUG_NEW en mode débogage, vous obtenez encore détection des fuites, mais sans le numéro de ligne de fichier source reporting décrites ci-dessus.

Si vous substituez opérateurs **nouveau** et **supprimer**, perd de cette fonctionnalité de diagnostique.

### <a name="example"></a>Exemple

Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans le `CObject` exemples.

[!code-cpp[NVC_MFCCObjectSample#15](../../mfc/codesnippet/cpp/cobject-class_8.cpp)]

##  <a name="operator_new"></a>  CObject::operator nouveau

Pour la version de la bibliothèque, opérateur **nouveau** effectue une allocation de mémoire optimale d’une manière similaire à `malloc`.

```
void* PASCAL operator new(size_t nSize);
void* PASCAL operator new(size_t, void* p);

void* PASCAL operator new(
    size_t nSize,
    LPCSTR lpszFileName,
    int nLine);
```

### <a name="remarks"></a>Notes

Dans la version Debug, opérateur **nouveau** participe à un schéma d’allocation de la surveillance conçu pour détecter les fuites de mémoire.

Si vous utilisez la ligne de code

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

avant tout vos implémentations d’un. CPP de fichiers, puis la deuxième version de **nouveau** doit être utilisé, en stockant le nom de fichier et numéro de ligne dans le bloc alloué pour générer un rapport ultérieur. Vous n’avez pas à vous soucier d’en fournissant les paramètres supplémentaires ; une macro s’occupe de cela pour vous.

Même si vous n’utilisez pas DEBUG_NEW en mode débogage, vous obtenez encore détection des fuites, mais sans le numéro de ligne de fichier source reporting décrites ci-dessus.

> [!NOTE]
>  Si vous substituez cet opérateur, vous devez également substituer **supprimer**. N’utilisez pas la bibliothèque standard `_new_handler` (fonction).

### <a name="example"></a>Exemple

Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans le `CObject` exemples.

[!code-cpp[NVC_MFCCObjectSample#16](../../mfc/codesnippet/cpp/cobject-class_9.h)]

##  <a name="serialize"></a>  CObject::Serialize

Lit ou écrit cet objet dans une archive.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Paramètres

*ar*<br/>
Un `CArchive` objet à sérialiser à partir d’ou.

### <a name="remarks"></a>Notes

Vous devez substituer `Serialize` pour chaque classe que vous souhaitez sérialiser. Substituées `Serialize` devez d’abord appeler la `Serialize` fonction de sa classe de base.

Vous devez également utiliser le [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) macro dans votre déclaration de classe et vous devez utiliser le [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) macro dans l’implémentation.

Utilisez [CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading) ou [CArchive::IsStoring](../../mfc/reference/carchive-class.md#isstoring) pour déterminer si l’archive est le chargement ou le stockage.

`Serialize` est appelée par [CArchive::ReadObject](../../mfc/reference/carchive-class.md#readobject) et [CArchive::WriteObject](../../mfc/reference/carchive-class.md#writeobject). Ces fonctions sont associées les `CArchive` opérateur d’insertion ( **< \<**) et l’opérateur d’extraction ( **>>**).

Pour des exemples de sérialisation, consultez l’article [sérialisation : sérialisation d’un objet](../../mfc/serialization-serializing-an-object.md).

### <a name="example"></a>Exemple

Consultez [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) pour obtenir la liste de la `CAge` classe utilisée dans tous les `CObject` exemples.

[!code-cpp[NVC_MFCCObjectSample#13](../../mfc/codesnippet/cpp/cobject-class_10.cpp)]

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)

