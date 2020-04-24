---
title: Classe CObject
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
ms.openlocfilehash: 66d76e0062d13b2bd5a16d9b07f99db9e989805a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753993"
---
# <a name="cobject-class"></a>Classe CObject

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
|[CObject::Dump](#dump)|Produit un dépotoir diagnostique de cet objet.|
|[CObject::GetRuntimeClass](#getruntimeclass)|Retourne `CRuntimeClass` la structure correspondant à la classe de cet objet.|
|[CObject::IsKindOf](#iskindof)|Teste la relation de cet objet avec une classe donnée.|
|[CObject::Isserializable](#isserializable)|Tests pour voir si cet objet peut être sérialisé.|
|[CObject::Serialize](#serialize)|Charge ou stocke un objet à partir d’une archive.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CObject::l’opérateur supprimer](#operator_delete)|Opérateur de **suppression** spécial.|
|[CObject::opérateur nouveau](#operator_new)|Nouvel **new** opérateur spécial.|

## <a name="remarks"></a>Notes

Il sert de racine non seulement `CFile` pour `CObList`les classes de bibliothèque telles que et , mais aussi pour les classes que vous écrivez. `CObject`fournit des services de base, y compris

- Soutien à la sérialisation

- Informations sur les cours de course

- Sortie diagnostique d’objet

- Compatibilité avec les classes de collecte

Notez `CObject` que ne prend pas en charge l’héritage multiple. Vos classes dérivées `CObject` peuvent n’avoir `CObject` qu’une seule classe de base, et cela doit être laissé le plus dans la hiérarchie. Il est toutefois permis d’avoir des `CObject`structures et des classes non dérivées dans des branches à héritage multiple de droite.

Vous réaliserez les `CObject` avantages majeurs de la dérivation si vous utilisez certaines des macros facultatives dans votre mise en œuvre de classe et des déclarations.

Les macros de premier niveau, [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic) et [IMPLEMENT_DYNAMIC,](run-time-object-model-services.md#implement_dynamic)permettent l’accès au nom de la classe et à sa position dans la hiérarchie. Ceci, à son tour, permet un dumping diagnostique significatif.

Les macros de deuxième niveau, [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) et [IMPLEMENT_SERIAL,](run-time-object-model-services.md#implement_serial)comprennent toutes les fonctionnalités des macros de premier niveau, et ils permettent à un objet d’être «sérialisé» à et à partir d’une «archive».

Pour plus d’informations sur le dépériment des `CObject`classes de la Fondation Microsoft et des classes de C en général et en utilisant , voir [Using CObject](../../mfc/using-cobject.md) and [Serialization](../../mfc/serialization-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CObject`

## <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="cobjectassertvalid"></a><a name="assertvalid"></a>CObject::AssertValid

Valide l’intégrité de cet objet.

```
virtual void AssertValid() const;
```

### <a name="remarks"></a>Notes

`AssertValid`effectue une vérification de validité sur cet objet en vérifiant son état interne. Dans la version Debug `AssertValid` de la bibliothèque, peut affirmer et ainsi mettre fin au programme avec un message qui énumère le numéro de ligne et le nom de fichier lorsque l’affirmation a échoué.

Lorsque vous écrivez votre propre classe, vous devez passer outre à la `AssertValid` fonction pour fournir des services de diagnostic pour vous-même et d’autres utilisateurs de votre classe. Le dépassement `AssertValid` appelle généralement `AssertValid` la fonction de sa classe de base avant de vérifier les membres de données uniques à la classe dérivée.

Parce `AssertValid` que c’est une fonction **de const,** vous n’êtes pas autorisé à changer l’état de l’objet pendant le test. Vos propres `AssertValid` fonctions de classe dérivées ne devraient pas jeter des exceptions mais doivent plutôt affirmer si elles détectent des données d’objet invalides.

La définition de la «validité» dépend de la classe de l’objet. En règle générale, la fonction doit effectuer une « vérification superficielle ». Autrement dit, si un objet contient des indications sur d’autres objets, il doit vérifier si les pointeurs ne sont pas nuls, mais il ne devrait pas effectuer des tests de validité sur les objets mentionnés par les pointeurs.

### <a name="example"></a>Exemple

Voir [CObList:CObList](../../mfc/reference/coblist-class.md#coblist) pour une `CAge` liste de `CObject` la classe utilisée dans tous les exemples.

[!code-cpp[NVC_MFCCObjectSample#7](../../mfc/codesnippet/cpp/cobject-class_1.cpp)]

Pour un autre exemple, voir [AfxDoForAllObjects](diagnostic-services.md#afxdoforallobjects).

## <a name="cobjectcobject"></a><a name="cobject"></a>CObject::CObject

Ces fonctions sont `CObject` les constructeurs standard.

```
CObject();
CObject(const CObject& objectSrc);
```

### <a name="parameters"></a>Paramètres

*objetSrc*<br/>
Une référence à un autre`CObject`

### <a name="remarks"></a>Notes

La version par défaut est automatiquement appelée par le constructeur de votre classe dérivée.

Si votre classe est sérialisable (elle intègre le IMPLEMENT_SERIAL macro), alors vous devez avoir un constructeur par défaut (un constructeur sans arguments) dans votre déclaration de classe. Si vous n’avez pas besoin d’un constructeur par défaut, déclarez un constructeur privé ou protégé « vide ». Pour plus d’informations, voir [Utiliser CObject](../../mfc/using-cobject.md).

Le constructeur standard de copie de classe par défaut de la classe CMD fait une copie membre par membre. La présence du `CObject` constructeur de copie privée garantit un message d’erreur de compilateur si le constructeur de copie de votre classe est nécessaire mais non disponible. Vous devez donc fournir un constructeur de copie si votre classe a besoin de cette capacité.

### <a name="example"></a>Exemple

Voir [CObList:CObList](../../mfc/reference/coblist-class.md#coblist) pour une `CAge` liste de `CObject` la classe utilisée dans les exemples.

[!code-cpp[NVC_MFCCObjectSample#8](../../mfc/codesnippet/cpp/cobject-class_2.cpp)]

## <a name="cobjectdump"></a><a name="dump"></a>CObject::Dump

Décharge le contenu de votre objet sur un objet [CDumpContext.](../../mfc/reference/cdumpcontext-class.md)

```
virtual void Dump(CDumpContext& dc) const;
```

### <a name="parameters"></a>Paramètres

*Dc*<br/>
Le contexte de décharge `afxDump`diagnostique pour le dumping, habituellement .

### <a name="remarks"></a>Notes

Lorsque vous écrivez votre propre classe, vous devez passer outre à la `Dump` fonction pour fournir des services de diagnostic pour vous-même et d’autres utilisateurs de votre classe. Le dépassement `Dump` appelle généralement `Dump` la fonction de sa classe de base avant d’imprimer des membres de données uniques à la classe dérivée. `CObject::Dump`imprime le nom de `IMPLEMENT_DYNAMIC` la classe si votre classe utilise la macro ou la IMPLEMENT_SERIAL.

> [!NOTE]
> Votre `Dump` fonction ne doit pas imprimer un caractère newline à la fin de sa sortie.

`Dump`appels n’ont de sens que dans la version Debug de la Microsoft Foundation Class Library. Vous devez entre parenthèses les appels, les déclarations de fonction et les implémentations de fonctions avec **#ifdef** /  `#endif` _DEBUG des énoncés pour la compilation conditionnelle.

Depuis `Dump` est une fonction **de const,** vous n’êtes pas autorisé à changer l’état d’objet pendant la décharge.

[L’opérateur d’insertion CDumpContext (<<)](../../mfc/reference/cdumpcontext-class.md#operator_lt_lt) appelle `Dump` lorsqu’un `CObject` pointeur est inséré.

`Dump`ne permet que le dumping "acyclique" d’objets. Vous pouvez vider une liste d’objets, par exemple, mais si l’un des objets est la liste elle-même, vous finirez par déborder la pile.

### <a name="example"></a>Exemple

Voir [CObList:CObList](../../mfc/reference/coblist-class.md#coblist) pour une `CAge` liste de `CObject` la classe utilisée dans tous les exemples.

[!code-cpp[NVC_MFCCObjectSample#9](../../mfc/codesnippet/cpp/cobject-class_3.cpp)]

## <a name="cobjectgetruntimeclass"></a><a name="getruntimeclass"></a>CObject::GetRuntimeClass

Retourne `CRuntimeClass` la structure correspondant à la classe de cet objet.

```
virtual CRuntimeClass* GetRuntimeClass() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur de la structure [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) correspondant à la classe de cet objet; jamais **NULL**.

### <a name="remarks"></a>Notes

Il y `CRuntimeClass` a `CObject`une structure pour chaque classe dérivée. Les membres de la structure sont les suivants :

- **m_lpszClassName LPCSTR** Une chaîne à durée nulle contenant le nom de classe ASCII.

- **int m_nObjectSize** La taille de l’objet, dans les octets. Si l’objet a des membres de données qui pointent vers la mémoire allouée, la taille de cette mémoire n’est pas incluse.

- **m_wSchema UINT** Le numéro de schéma (- 1 pour les classes non-étialisables). Voir le [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) macro pour une description du nombre de schémas.

- **CObject\* (\* PASCAL m_pfnCreateObject )) )** Un pointeur de fonction au constructeur par défaut qui crée un objet de votre classe (valable uniquement si la classe prend en charge la création dynamique; sinon, retourne **NULL**).

- **CRuntimeClass\* (\* PASCAL m_pfn_GetBaseClass )) )** Si votre application est dynamiquement liée à la version AFXDLL `CRuntimeClass` de MFC, un pointeur d’une fonction qui renvoie la structure de la classe de base.

- **CRuntimeClass\* m_pBaseClass** Si votre application est statiquement liée à MFC, un pointeur à la `CRuntimeClass` structure de la classe de base.

Cette fonction nécessite l’utilisation de la [IMPLEMENT_DYNAMIC,](run-time-object-model-services.md#implement_dynamic) [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate), ou [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) macro dans la mise en œuvre de la classe. Vous obtiendrez des résultats incorrects autrement.

### <a name="example"></a>Exemple

Voir [CObList:CObList](../../mfc/reference/coblist-class.md#coblist) pour une `CAge` liste de `CObject` la classe utilisée dans tous les exemples.

[!code-cpp[NVC_MFCCObjectSample#10](../../mfc/codesnippet/cpp/cobject-class_4.cpp)]

## <a name="cobjectiskindof"></a><a name="iskindof"></a>CObject::IsKindOf

Teste la relation de cet objet avec une classe donnée.

```
BOOL IsKindOf(const CRuntimeClass* pClass) const;
```

### <a name="parameters"></a>Paramètres

*pClasse*<br/>
Un pointeur d’une structure [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) associée à votre `CObject`classe dérivée.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’objet correspond à la classe; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction *teste pClass* pour voir si (1) il s’agit d’un objet de la classe spécifiée ou (2) il s’agit d’un objet d’une classe dérivée de la classe spécifiée. Cette fonction ne fonctionne que pour les classes déclarées avec le [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic), [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate), ou [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) macro.

N’utilisez pas cette fonction intensivement parce qu’elle va à l’encontre de la fonction de polymorphisme C. Utilisez plutôt des fonctions virtuelles.

### <a name="example"></a>Exemple

Voir [CObList:CObList](../../mfc/reference/coblist-class.md#coblist) pour une `CAge` liste de `CObject` la classe utilisée dans tous les exemples.

[!code-cpp[NVC_MFCCObjectSample#11](../../mfc/codesnippet/cpp/cobject-class_5.cpp)]

## <a name="cobjectisserializable"></a><a name="isserializable"></a>CObject::Isserializable

Testez si cet objet est admissible à la sérialisation.

```
BOOL IsSerializable() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si cet objet peut être sérialisé; sinon 0.

### <a name="remarks"></a>Notes

Pour qu’une classe soit sérialisable, sa déclaration doit contenir la [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) macro, et la mise en œuvre doit contenir la [macro IMPLEMENT_SERIAL.](run-time-object-model-services.md#implement_serial)

> [!NOTE]
> Ne remplacez pas cette fonction.

### <a name="example"></a>Exemple

Voir [CObList:CObList](../../mfc/reference/coblist-class.md#coblist) pour une `CAge` liste de `CObject` la classe utilisée dans tous les exemples.

[!code-cpp[NVC_MFCCObjectSample#12](../../mfc/codesnippet/cpp/cobject-class_6.cpp)]

## <a name="cobjectoperator-delete"></a><a name="operator_delete"></a>CObject::l’opérateur supprimer

Pour la version Libération de la bibliothèque, l’opérateur **supprime** la mémoire allouée par l’opérateur **nouveau**.

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

Dans la version Debug, l’opérateur **supprimer** participe à un système de surveillance de l’allocation conçu pour détecter les fuites de mémoire.

Si vous utilisez la ligne de code

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

avant l’une de vos implémentations dans un . Le fichier du RPC, puis la troisième version de **la suppression** seront utilisés, en stockant le nom de fichier et le numéro de ligne dans le bloc alloué pour les rapports ultérieurs. Vous n’avez pas à vous soucier de fournir les paramètres supplémentaires; une macro s’en occupe pour vous.

Même si vous n’utilisez pas DEBUG_NEW en mode Debug, vous obtenez toujours la détection des fuites, mais sans les rapports de numéro de ligne de fichier source décrits ci-dessus.

Si vous remplacez les opérateurs **nouveaux** et **supprimez,** vous perdez cette capacité de diagnostic.

### <a name="example"></a>Exemple

Voir [CObList:CObList](../../mfc/reference/coblist-class.md#coblist) pour une `CAge` liste de `CObject` la classe utilisée dans les exemples.

[!code-cpp[NVC_MFCCObjectSample#15](../../mfc/codesnippet/cpp/cobject-class_8.cpp)]

## <a name="cobjectoperator-new"></a><a name="operator_new"></a>CObject::opérateur nouveau

Pour la version Libération de la bibliothèque, l’opérateur **nouveau** `malloc`effectue une allocation de mémoire optimale d’une manière similaire à .

```cpp
void* PASCAL operator new(size_t nSize);
void* PASCAL operator new(size_t, void* p);

void* PASCAL operator new(
    size_t nSize,
    LPCSTR lpszFileName,
    int nLine);
```

### <a name="remarks"></a>Notes

Dans la version Debug, l’opérateur **new** participe à un système de surveillance de l’allocation conçu pour détecter les fuites de mémoire.

Si vous utilisez la ligne de code

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

avant l’une de vos implémentations dans un . Le fichier du RPC, puis la deuxième version du **nouveau,** seront utilisés, en stockant le nom de fichier et le numéro de ligne dans le bloc alloué pour les rapports ultérieurs. Vous n’avez pas à vous soucier de fournir les paramètres supplémentaires; une macro s’en occupe pour vous.

Même si vous n’utilisez pas DEBUG_NEW en mode Debug, vous obtenez toujours la détection des fuites, mais sans les rapports de numéro de ligne de fichier source décrits ci-dessus.

> [!NOTE]
> Si vous remplacez cet opérateur, vous devez également remplacer **supprimer**. N’utilisez pas `_new_handler` la fonction de bibliothèque standard.

### <a name="example"></a>Exemple

Voir [CObList:CObList](../../mfc/reference/coblist-class.md#coblist) pour une `CAge` liste de `CObject` la classe utilisée dans les exemples.

[!code-cpp[NVC_MFCCObjectSample#16](../../mfc/codesnippet/cpp/cobject-class_9.h)]

## <a name="cobjectserialize"></a><a name="serialize"></a>CObject::Serialize

Lit ou écrit cet objet dans une archive.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Paramètres

*Ar*<br/>
Un `CArchive` objet à sérialiser vers ou depuis.

### <a name="remarks"></a>Notes

Vous devez `Serialize` passer outre à chaque classe que vous avez l’intention de sérialiser. Le dépassement `Serialize` doit d’abord appeler la `Serialize` fonction de sa classe de base.

Vous devez également utiliser la [macro DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) dans votre déclaration de classe, et vous devez utiliser la [macro IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) dans la mise en œuvre.

Utilisez [CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading) ou [CArchive::IsStoring](../../mfc/reference/carchive-class.md#isstoring) pour déterminer si l’archive est le chargement ou le stockage.

`Serialize`est appelé par [CArchive::ReadObject](../../mfc/reference/carchive-class.md#readobject) et [CArchive::WriteObject](../../mfc/reference/carchive-class.md#writeobject). Ces fonctions sont `CArchive` associées à ** < **l’opérateur **>>** d’insertion ( ) et à l’opérateur d’extraction ( ).

Pour des exemples de sérialisation, voir l’article [Serialization: Serializing an Object](../../mfc/serialization-serializing-an-object.md).

### <a name="example"></a>Exemple

Voir [CObList:CObList](../../mfc/reference/coblist-class.md#coblist) pour une `CAge` liste de `CObject` la classe utilisée dans tous les exemples.

[!code-cpp[NVC_MFCCObjectSample#13](../../mfc/codesnippet/cpp/cobject-class_10.cpp)]

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
