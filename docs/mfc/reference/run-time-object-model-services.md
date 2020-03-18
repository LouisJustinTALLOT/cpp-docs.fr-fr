---
title: Services du modèle objet au moment de l'exécution
ms.date: 03/27/2019
helpviewer_keywords:
- run-time object model services macros
ms.assetid: 4a3e79df-2ee3-43a4-8193-20298828de85
ms.openlocfilehash: a4e471decd07cb2025b833513403b64f43105d0c
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446440"
---
# <a name="run-time-object-model-services"></a>Services du modèle objet au moment de l'exécution

Les classes [CObject](../../mfc/reference/cobject-class.md) et [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) encapsulent plusieurs services Object, y compris l’accès aux informations de classe au moment de l’exécution, la sérialisation et la création d’objets dynamiques. Toutes les classes dérivées de `CObject` héritent de cette fonctionnalité.

L'accès aux informations sur la classe d'exécution vous permet de déterminer les informations sur une classe d'objets au moment de l'exécution. La capacité de déterminer la classe d'un objet au moment de l'exécution est utile lorsque vous avez besoin de vérifications de type supplémentaires d'arguments de fonction et lorsque vous devez écrire un code spécial en fonction de la classe d'un objet. Les informations sur la classe d'exécution ne sont pas prises en charge directement par le langage C++.

La sérialisation est le processus d'écriture ou de lecture du contenu d'un objet vers et à partir d'un fichier. Vous pouvez utiliser la sérialisation pour stocker le contenu d'un objet même après que l'application se termine. L'objet peut ensuite être lu à partir du fichier lorsque l'application est redémarrée. De tels objets de données sont dits "persistants".

La création d'objets dynamique permet de créer un objet d'une classe spécifiée au moment de l'exécution. Par exemple, les objets document, vue et frame doivent prendre en charge la création dynamique car le framework doit les créer dynamiquement.

Le tableau suivant répertorie les macros MFC qui prennent en charge les informations relatives à la classe au moment de l'exécution, la sérialisation et la création dynamique.

Pour plus d’informations sur ces services d’objets au moment de l’exécution et la sérialisation, consultez l’article [CObject, classe : accès aux informations de classe d’exécution](../../mfc/accessing-run-time-class-information.md).

### <a name="run-time-object-model-services-macros"></a>Macros des services du modèle objet au moment de l'exécution

|||
|-|-|
|[DECLARE_DYNAMIC](#declare_dynamic)|Permet d'accéder aux informations sur la classe d'exécution (doit être utilisé dans la déclaration de classe).|
|[DECLARE_DYNCREATE](#declare_dyncreate)|Permet la création dynamique et l'accès aux informations sur la classe d'exécution (doit être utilisé dans la déclaration de classe).|
|[DECLARE_SERIAL](#declare_serial)|Permet la sérialisation dynamique et l'accès aux informations sur la classe d'exécution (doit être utilisé dans la déclaration de classe).|
|[IMPLEMENT_DYNAMIC](#implement_dynamic)|Permet d'accéder aux informations sur la classe d'exécution (doit être utilisé dans l'implémentation de classe).|
|[IMPLEMENT_DYNCREATE](#implement_dyncreate)|Permet la création dynamique et l'accès aux informations sur la classe d'exécution (doit être utilisé dans l'implémentation de classe).|
|[IMPLEMENT_SERIAL](#implement_serial)|Permet la sérialisation et l'accès aux informations sur la classe d'exécution (doit être utilisé dans l'implémentation de classe).|
|[RUNTIME_CLASS](#runtime_class)|Retourne la structure `CRuntimeClass` qui correspond à la classe nommée.|

OLE requiert souvent la création dynamique des objets au moment de l'exécution. Par exemple, une application serveur OLE doit pouvoir créer des éléments OLE dynamiquement en réponse à la demande d'un client. De même, un serveur Automation doit être en mesure de créer des éléments en réponse aux demandes des clients Automation.

La bibliothèque MFC fournit deux macros spécifiques à OLE.

### <a name="dynamic-creation-of-ole-objects"></a>Création dynamique des objets OLE

|||
|-|-|
|[AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)|Détermine si la bibliothèque de contrôles communs implémente l’API spécifiée.|
|[AFX_COMCTL32_IF_EXISTS2](#afx_comctl32_if_exists2)|Détermine si la bibliothèque de contrôles communs implémente l’API spécifiée.|
|[DECLARE_OLECREATE](#declare_olecreate)|Active les objets à créer par l'intermédiaire de OLE Automation.|
|[DECLARE_OLECTLTYPE](#declare_olectltype)|Déclare les fonctions membres `GetUserTypeNameID` et `GetMiscStatus` de votre classe de contrôle.|
|[DECLARE_PROPPAGEIDS](#declare_proppageids)|Déclare que le contrôle OLE fournit une liste de pages de propriétés pour afficher ses propriétés.|
|[IMPLEMENT_OLECREATE](#implement_olecreate)|Active les objets à créer par le système OLE.|
|[IMPLEMENT_OLECTLTYPE](#implement_olectltype)|Implémente les fonctions membres `GetUserTypeNameID` et `GetMiscStatus` de votre classe de contrôle.|
|[IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags)|Cette macro ou [IMPLEMENT_OLECREATE](#implement_olecreate) doit apparaître dans le fichier d’implémentation pour toute classe qui utilise `DECLARE_OLECREATE`. |

## <a name="afx_comctl32_if_exists"></a>AFX_COMCTL32_IF_EXISTS

Détermine si la bibliothèque de contrôles communs implémente l’API spécifiée.

### <a name="syntax"></a>Syntaxe

```
AFX_COMCTL32_IF_EXISTS(  proc );
```

### <a name="parameters"></a>Paramètres

*proc*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui contient le nom de la fonction, ou spécifie la valeur ordinale de la fonction. Si ce paramètre est une valeur ordinale, il doit figurer dans le mot de poids faible ; le mot de poids fort doit être égal à zéro. Ce paramètre doit être au format Unicode.

### <a name="remarks"></a>Notes

Utilisez cette macro pour déterminer si la bibliothèque de contrôles communs est la fonction spécifiée par *proc* (au lieu d’appeler [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress).

### <a name="requirements"></a>Spécifications

afxcomctl32.h, afxcomctl32.inl

## <a name="afx_comctl32_if_exists2"></a>AFX_COMCTL32_IF_EXISTS2

Détermine si la bibliothèque de contrôles communs implémente l’API spécifiée (il s’agit de la version Unicode de [AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)).

### <a name="syntax"></a>Syntaxe

```
AFX_COMCTL32_IF_EXISTS2( proc );
```

### <a name="parameters"></a>Paramètres

*proc*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui contient le nom de la fonction, ou spécifie la valeur ordinale de la fonction. Si ce paramètre est une valeur ordinale, il doit figurer dans le mot de poids faible ; le mot de poids fort doit être égal à zéro. Ce paramètre doit être au format Unicode.

### <a name="remarks"></a>Notes

Utilisez cette macro pour déterminer si la bibliothèque de contrôles communs est la fonction spécifiée par *proc* (au lieu d’appeler [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress). Cette macro est la version Unicode de AFX_COMCTL32_IF_EXISTS.

### <a name="requirements"></a>Spécifications

afxcomctl32.h, afxcomctl32.inl

##  <a name="declare_dynamic"></a>DECLARE_DYNAMIC

Ajoute la possibilité d’accéder aux informations d’exécution relatives à la classe d’un objet lors de la dérivation d’une classe à partir de `CObject`.

```
DECLARE_DYNAMIC(class_name)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Nom réel de la classe.

### <a name="remarks"></a>Notes

Ajoutez la macro DECLARE_DYNAMIC au module d’en-tête (. h) de la classe, puis incluez ce module dans tous les modules. cpp qui ont besoin d’accéder aux objets de cette classe.

Si vous utilisez la DECLARE_ macros dynamiques et IMPLEMENT_DYNAMIC comme décrit, vous pouvez utiliser la macro RUNTIME_CLASS et la fonction `CObject::IsKindOf` pour déterminer la classe de vos objets au moment de l’exécution.

Si DECLARE_DYNAMIC est inclus dans la déclaration de classe, IMPLEMENT_DYNAMIC doit être inclus dans l’implémentation de la classe.

Pour plus d’informations sur la macro DECLARE_DYNAMIC, consultez [rubriques relatives aux classes CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Exemple

Consultez l’exemple de [IMPLEMENT_DYNAMIC](#implement_dynamic).

### <a name="requirements"></a>Spécifications

**En-tête :** afx.h

##  <a name="declare_dyncreate"></a>DECLARE_DYNCREATE

Permet de créer dynamiquement des objets de classes dérivées d' `CObject`au moment de l’exécution.

```
DECLARE_DYNCREATE(class_name)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Nom réel de la classe.

### <a name="remarks"></a>Notes

L’infrastructure utilise cette capacité pour créer dynamiquement des objets. Par exemple, la nouvelle vue créée lorsque vous ouvrez un nouveau document. Les classes document, vue et Frame doivent prendre en charge la création dynamique, car le Framework doit les créer dynamiquement.

Ajoutez la macro DECLARE_DYNCREATE dans le module. h pour la classe, puis incluez ce module dans tous les modules. cpp qui ont besoin d’accéder aux objets de cette classe.

Si DECLARE_DYNCREATE est inclus dans la déclaration de classe, IMPLEMENT_DYNCREATE doit être inclus dans l’implémentation de la classe.

Pour plus d’informations sur la macro DECLARE_DYNCREATE, consultez [rubriques relatives aux classes CObject](../../mfc/using-cobject.md).

> [!NOTE]
>  La macro DECLARE_DYNCREATE comprend toutes les fonctionnalités de DECLARE_DYNAMIC.

### <a name="example"></a>Exemple

Consultez l’exemple de [IMPLEMENT_DYNCREATE](#implement_dyncreate).

### <a name="requirements"></a>Spécifications

**En-tête :** afx.h

## <a name="declare_olectltype"></a>DECLARE_OLECTLTYPE

Déclare les fonctions membres `GetUserTypeNameID` et `GetMiscStatus` de votre classe de contrôle.

### <a name="syntax"></a>Syntaxe

```
DECLARE_OLECTLTYPE( class_name )
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Nom de la classe de contrôle.

### <a name="remarks"></a>Notes

`GetUserTypeNameID` et `GetMiscStatus` sont des fonctions virtuelles pures, déclarées dans `COleControl`. Étant donné que ces fonctions sont virtuelles pures, elles doivent être remplacées dans votre classe de contrôle. En plus de DECLARE_OLECTLTYPE, vous devez ajouter la macro IMPLEMENT_OLECTLTYPE à votre déclaration de classe de contrôle.

### <a name="requirements"></a>Spécifications

**En-tête :** afxctl. h

## <a name="declare_proppageids"></a>DECLARE_PROPPAGEIDS

Déclare que le contrôle OLE fournit une liste de pages de propriétés pour afficher ses propriétés.

### <a name="syntax"></a>Syntaxe

```
DECLARE_PROPPAGEIDS( class_name )
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Nom de la classe de contrôle qui possède les pages de propriétés.

### <a name="remarks"></a>Notes

Utilisez la macro `DECLARE_PROPPAGEIDS` à la fin de votre déclaration de classe. Ensuite, dans le fichier. cpp qui définit les fonctions membres de la classe, utilisez la macro `BEGIN_PROPPAGEIDS`, les entrées de macro pour chacune des pages de propriétés de votre contrôle, et la macro `END_PROPPAGEIDS` pour déclarer la fin de la liste des pages de propriétés.

Pour plus d’informations sur les pages de propriétés, consultez l’article [contrôles ActiveX : pages de propriétés](../mfc-activex-controls-property-pages.md).

### <a name="requirements"></a>Spécifications

**En-tête :** afxctl. h

##  <a name="declare_serial"></a>DECLARE_SERIAL

Génère le C++ code d’en-tête nécessaire pour une classe dérivée de `CObject`qui peut être sérialisée.

```
DECLARE_SERIAL(class_name)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Nom réel de la classe.

### <a name="remarks"></a>Notes

La sérialisation est le processus qui consiste à écrire ou à lire le contenu d’un objet dans un fichier.

Utilisez la macro DECLARE_SERIAL dans un module. h, puis incluez ce module dans tous les modules. cpp qui requièrent l’accès aux objets de cette classe.

Si DECLARE_SERIAL est inclus dans la déclaration de classe, IMPLEMENT_SERIAL doit être inclus dans l’implémentation de la classe.

La macro DECLARE_SERIAL comprend toutes les fonctionnalités de DECLARE_DYNAMIC et de DECLARE_DYNCREATE.

Vous pouvez utiliser la macro AFX_API pour exporter automatiquement l’opérateur d’extraction `CArchive` pour les classes qui utilisent les macros DECLARE_SERIAL et IMPLEMENT_SERIAL. Faites défiler les déclarations de classe (situées dans le fichier. h) avec le code suivant :

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

Pour plus d’informations sur la macro DECLARE_SERIAL, consultez [rubriques relatives aux classes CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCObjectSample#21](../../mfc/codesnippet/cpp/run-time-object-model-services_2.h)]

### <a name="requirements"></a>Spécifications

**En-tête :** afx.h

##  <a name="implement_dynamic"></a>IMPLEMENT_DYNAMIC

Génère le C++ code nécessaire pour une classe dynamique dérivée de `CObject`avec un accès au moment de l’exécution au nom et à la position de la classe dans la hiérarchie.

```
IMPLEMENT_DYNAMIC(class_name, base_class_name)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Nom réel de la classe.

*base_class_name*<br/>
Nom de la classe de base.

### <a name="remarks"></a>Notes

Utilisez la macro IMPLEMENT_DYNAMIC dans un module. cpp, puis liez le code objet résultant une seule fois.

Pour plus d’informations, consultez [rubriques relatives aux classes CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCObjectSample#2](../../mfc/codesnippet/cpp/run-time-object-model-services_3.h)]

[!code-cpp[NVC_MFCCObjectSample#3](../../mfc/codesnippet/cpp/run-time-object-model-services_4.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête :** afx.h

##  <a name="implement_dyncreate"></a>IMPLEMENT_DYNCREATE

Permet de créer des objets de classes dérivées de `CObject`dynamiquement au moment de l’exécution lorsqu’ils sont utilisés avec la macro DECLARE_DYNCREATE.

```
IMPLEMENT_DYNCREATE(class_name, base_class_name)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Nom réel de la classe.

*base_class_name*<br/>
Nom réel de la classe de base.

### <a name="remarks"></a>Notes

L’infrastructure utilise cette capacité pour créer dynamiquement des objets, par exemple, lorsqu’il lit un objet à partir du disque pendant la sérialisation. Ajoutez la macro IMPLEMENT_DYNCREATE dans le fichier d’implémentation de classe. Pour plus d’informations, consultez [rubriques relatives aux classes CObject](../../mfc/using-cobject.md).

Si vous utilisez les macros DECLARE_DYNCREATE et IMPLEMENT_DYNCREATE, vous pouvez utiliser la macro RUNTIME_CLASS et la fonction membre `CObject::IsKindOf` pour déterminer la classe de vos objets au moment de l’exécution.

Si DECLARE_DYNCREATE est inclus dans la déclaration de classe, IMPLEMENT_DYNCREATE doit être inclus dans l’implémentation de la classe.

Notez que cette définition de macro appellera le constructeur par défaut pour votre classe. Si un constructeur non trivial est explicitement implémenté par la classe, il doit également implémenter explicitement le constructeur par défaut. Le constructeur par défaut peut être ajouté aux sections **privées** ou membres **protégées** de la classe pour empêcher son appel à partir de l’extérieur de l’implémentation de la classe.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCObjectSample#22](../../mfc/codesnippet/cpp/run-time-object-model-services_5.h)]

[!code-cpp[NVC_MFCCObjectSample#23](../../mfc/codesnippet/cpp/run-time-object-model-services_6.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête :** afx.h

## <a name="implement_olecreate_flags"></a>IMPLEMENT_OLECREATE_FLAGS

Cette macro ou [IMPLEMENT_OLECREATE](#implement_olecreate) doit apparaître dans le fichier d’implémentation pour toute classe qui utilise DECLARE_OLECREATE.

### <a name="syntax"></a>Syntaxe

```
IMPLEMENT_OLECREATE_FLAGS( class_name, external_name, nFlags,
    l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Nom réel de la classe.

*external_name*<br/>
Nom de l’objet exposé à d’autres applications (entre guillemets).

*nFlags*<br/>
Contient un ou plusieurs des indicateurs suivants :

- `afxRegInsertable` permet d’afficher le contrôle dans la boîte de dialogue Insérer un objet pour les objets OLE.
- `afxRegApartmentThreading` définit le modèle de thread dans le registre sur ThreadingModel = Apartment.
- `afxRegFreeThreading` définit le modèle de thread dans le registre sur ThreadingModel = Free.

Vous pouvez combiner les deux indicateurs `afxRegApartmentThreading` et `afxRegFreeThreading` pour définir ThreadingModel = both. Pour plus d’informations sur l’inscription du modèle de thread, consultez [InprocServer32](/windows/win32/com/inprocserver32) dans le SDK Windows.

composants *l*, *W1*, *W2*, *B1*, *B2*, *B3*, *B4*, *B5*, *B6*, *B7*et *B8* du CLSID de la classe.

### <a name="remarks"></a>Notes

> [!NOTE]
>  Si vous utilisez IMPLEMENT_OLECREATE_FLAGS, vous pouvez spécifier le modèle de thread pris en charge par votre objet à l’aide du paramètre *nFlags* . Si vous ne souhaitez prendre en charge que le modèle de simple-roulement, utilisez IMPLEMENT_OLECREATE.

Le nom externe est l’identificateur exposé à d’autres applications. Les applications clientes utilisent le nom externe pour demander un objet de cette classe à un serveur Automation.

L’ID de classe OLE est un identificateur 128 bits unique pour l’objet. Il se compose d' **un long**, de deux **mots**et de huit **octets**, représentés par *l*, *W1*, *W2*et *B1* à *B8* dans la description de la syntaxe. L’Assistant Application et les assistants code créent des ID de classe OLE uniques pour vous en fonction des besoins.

### <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="implement_olectltype"></a>IMPLEMENT_OLECTLTYPE

Implémente les fonctions membres `GetUserTypeNameID` et `GetMiscStatus` de votre classe de contrôle.

### <a name="syntax"></a>Syntaxe

```
DECLARE_OLECTLTYPE( class_name, idsUserTypeName, dwOleMisc )
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Nom de la classe de contrôle.

*idsUserTypeName*<br/>
ID de ressource d’une chaîne contenant le nom externe du contrôle.

*dwOleMisc*<br/>
Énumération contenant un ou plusieurs indicateurs. Pour plus d’informations sur cette énumération, consultez [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) dans le SDK Windows.

### <a name="remarks"></a>Notes

En plus de IMPLEMENT_OLECTLTYPE, vous devez ajouter la macro DECLARE_OLECTLTYPE à votre déclaration de classe de contrôle.

La fonction membre `GetUserTypeNameID` retourne la chaîne de ressource qui identifie votre classe de contrôle. `GetMiscStatus` retourne les bits OLEMISC pour votre contrôle. Cette énumération spécifie une collection de paramètres décrivant diverses caractéristiques de votre contrôle. Pour obtenir une description complète des paramètres OLEMISC, consultez [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) dans la SDK Windows.

> [!NOTE]
>  Les paramètres par défaut utilisés par le ControlWizard ActiveX sont : OLEMISC_ACTIVATEWHENVISIBLE, OLEMISC_SETCLIENTSITEFIRST, OLEMISC_INSIDEOUT, OLEMISC_CANTLINKINSIDE et OLEMISC_RECOMPOSEONRESIZE.

### <a name="requirements"></a>Spécifications

**En-tête :** afxctl. h

##  <a name="implement_serial"></a>IMPLEMENT_SERIAL

Génère le C++ code nécessaire pour une classe dynamique dérivée de `CObject`avec un accès au moment de l’exécution au nom et à la position de la classe dans la hiérarchie.

```
IMPLEMENT_SERIAL(class_name, base_class_name, wSchema)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Nom réel de la classe.

*base_class_name*<br/>
Nom de la classe de base.

*wSchema*<br/>
« Numéro de version » UINT qui sera encodé dans l’Archive pour permettre à un programme de désérialisation d’identifier et de gérer les données créées par les versions antérieures du programme. Le numéro de schéma de la classe ne doit pas être-1.

### <a name="remarks"></a>Notes

Utilisez la macro IMPLEMENT_SERIAL dans un module. cpp ; Liez ensuite le code objet résultant une seule fois.

Vous pouvez utiliser la macro AFX_API pour exporter automatiquement l’opérateur d’extraction `CArchive` pour les classes qui utilisent les macros DECLARE_SERIAL et IMPLEMENT_SERIAL. Faites défiler les déclarations de classe (situées dans le fichier. h) avec le code suivant :

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

Pour plus d’informations, consultez les rubriques de la [classe CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCObjectSample#24](../../mfc/codesnippet/cpp/run-time-object-model-services_7.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête :** afx.h

##  <a name="runtime_class"></a>RUNTIME_CLASS

Obtient la structure de classe au moment de l’exécution à partir C++ du nom d’une classe.

```
RUNTIME_CLASS(class_name)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Nom réel de la classe (non placé entre guillemets).

### <a name="remarks"></a>Notes

RUNTIME_CLASS retourne un pointeur vers une structure [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) pour la classe spécifiée par *class_name*. Seules les classes dérivées de `CObject`déclarées avec DECLARE_DYNAMIC, DECLARE_DYNCREATE ou DECLARE_SERIAL retournent des pointeurs vers une structure `CRuntimeClass`.

Pour plus d’informations, consultez [rubriques relatives aux classes CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCObjectSample#25](../../mfc/codesnippet/cpp/run-time-object-model-services_8.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête :** afx.h

##  <a name="declare_olecreate"></a>DECLARE_OLECREATE

Permet de créer des objets de classes dérivées d' `CCmdTarget`par le biais d’OLE Automation.

```
DECLARE_OLECREATE(class_name)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Nom réel de la classe.

### <a name="remarks"></a>Notes

Cette macro permet à d’autres applications compatibles OLE de créer des objets de ce type.

Ajoutez la macro DECLARE_OLECREATE dans le module. h pour la classe, puis incluez ce module dans tous les modules. cpp qui ont besoin d’accéder aux objets de cette classe.

Si DECLARE_OLECREATE est inclus dans la déclaration de classe, IMPLEMENT_OLECREATE doit être inclus dans l’implémentation de la classe. Une déclaration de classe utilisant DECLARE_OLECREATE doit également utiliser DECLARE_DYNCREATE ou DECLARE_SERIAL.

### <a name="requirements"></a>Spécifications

**En-tête**: afxdisp. h

##  <a name="implement_olecreate"></a>IMPLEMENT_OLECREATE

Cette macro ou [IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags) doit apparaître dans le fichier d’implémentation pour toute classe qui utilise `DECLARE_OLECREATE`.

```
IMPLEMENT_OLECREATE(class_name, external_name, l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Nom réel de la classe.

*external_name*<br/>
Nom de l’objet exposé à d’autres applications (entre guillemets).

composants *l*, *W1*, *W2*, *B1*, *B2*, *B3*, *B4*, *B5*, *B6*, *B7*et *B8* du CLSID de la classe.

### <a name="remarks"></a>Notes

> [!NOTE]
>  Si vous utilisez IMPLEMENT_OLECREATE, par défaut, vous ne prenez en charge que le modèle à thread unique. Si vous utilisez IMPLEMENT_OLECREATE_FLAGS, vous pouvez spécifier le modèle de thread pris en charge par votre objet à l’aide du paramètre *nFlags* .

Le nom externe est l’identificateur exposé à d’autres applications. Les applications clientes utilisent le nom externe pour demander un objet de cette classe à un serveur Automation.

L’ID de classe OLE est un identificateur 128 bits unique pour l’objet. Il se compose d' **un long**, de deux **mots**et de huit **octets**, représentés par *l*, *W1*, *W2*et *B1* à *B8* dans la description de la syntaxe. L’Assistant Application et les assistants code créent des ID de classe OLE uniques pour vous en fonction des besoins.

### <a name="requirements"></a>Spécifications

**En-tête**: afxdisp. h

## <a name="see-also"></a>Voir aussi

[Macros et globales](mfc-macros-and-globals.md)<br/>
[Isolement de la bibliothèque de contrôles communs MFC](../isolation-of-the-mfc-common-controls-library.md)<br/>
[Clé CLSID](/windows/win32/com/clsid-key-hklm)
