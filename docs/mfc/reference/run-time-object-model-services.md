---
title: Services du modèle objet au moment de l'exécution
ms.date: 03/27/2019
helpviewer_keywords:
- run-time object model services macros
ms.assetid: 4a3e79df-2ee3-43a4-8193-20298828de85
ms.openlocfilehash: f1cefdad368ebcd006dcb4ecf653247147f36d03
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372940"
---
# <a name="run-time-object-model-services"></a>Services du modèle objet au moment de l'exécution

Les classes [CObject](../../mfc/reference/cobject-class.md) et [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) résument plusieurs services d’objets, y compris l’accès à des informations de classe en cours d’exécution, la sérialisation et la création d’objets dynamiques. Toutes les classes dérivées de `CObject` héritent de cette fonctionnalité.

L'accès aux informations sur la classe d'exécution vous permet de déterminer les informations sur une classe d'objets au moment de l'exécution. La capacité de déterminer la classe d'un objet au moment de l'exécution est utile lorsque vous avez besoin de vérifications de type supplémentaires d'arguments de fonction et lorsque vous devez écrire un code spécial en fonction de la classe d'un objet. Les informations sur la classe d'exécution ne sont pas prises en charge directement par le langage C++.

La sérialisation est le processus d'écriture ou de lecture du contenu d'un objet vers et à partir d'un fichier. Vous pouvez utiliser la sérialisation pour stocker le contenu d'un objet même après que l'application se termine. L'objet peut ensuite être lu à partir du fichier lorsque l'application est redémarrée. De tels objets de données sont dits "persistants".

La création d'objets dynamique permet de créer un objet d'une classe spécifiée au moment de l'exécution. Par exemple, les objets document, vue et frame doivent prendre en charge la création dynamique car le framework doit les créer dynamiquement.

Le tableau suivant répertorie les macros MFC qui prennent en charge les informations relatives à la classe au moment de l'exécution, la sérialisation et la création dynamique.

Pour plus d’informations sur ces services d’objets en temps d’exécution et la sérialisation, consultez l’article [CObject Class: Accessing Run-Time Class Information](../../mfc/accessing-run-time-class-information.md).

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
|[AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)|Détermine si la bibliothèque de contrôles communs met en œuvre l’API spécifiée.|
|[AFX_COMCTL32_IF_EXISTS2](#afx_comctl32_if_exists2)|Détermine si la bibliothèque de contrôles communs met en œuvre l’API spécifiée.|
|[DECLARE_OLECREATE](#declare_olecreate)|Active les objets à créer par l'intermédiaire de OLE Automation.|
|[DECLARE_OLECTLTYPE](#declare_olectltype)|Déclare les `GetUserTypeNameID` `GetMiscStatus` fonctions et les membres de votre classe de contrôle.|
|[DECLARE_PROPPAGEIDS](#declare_proppageids)|Déclare que le contrôle OLE fournit une liste de pages de propriété pour afficher ses propriétés.|
|[IMPLEMENT_OLECREATE](#implement_olecreate)|Active les objets à créer par le système OLE.|
|[IMPLEMENT_OLECTLTYPE](#implement_olectltype)|Implémente `GetMiscStatus` les fonctions et les `GetUserTypeNameID` membres de votre classe de contrôle.|
|[IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags)|Cette macro ou [IMPLEMENT_OLECREATE](#implement_olecreate) doit apparaître dans le fichier d’implémentation de toute classe qui utilise `DECLARE_OLECREATE`. |

## <a name="afx_comctl32_if_exists"></a><a name="afx_comctl32_if_exists"></a>AFX_COMCTL32_IF_EXISTS

Détermine si la bibliothèque de contrôles communs met en œuvre l’API spécifiée.

### <a name="syntax"></a>Syntaxe

```
AFX_COMCTL32_IF_EXISTS(  proc );
```

### <a name="parameters"></a>Paramètres

*proc*<br/>
Pointer vers une chaîne non terminée contenant le nom de la fonction, ou spécifie la valeur ordinaire de la fonction. Si ce paramètre est une valeur ordinaire, il doit être dans le mot de bas ordre; le mot de haut ordre doit être nul. Ce paramètre doit être dans Unicode.

### <a name="remarks"></a>Notes

Utilisez cette macro pour déterminer si la bibliothèque Common Controls la fonction spécifiée par *proc* (au lieu d’appeler [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress).

### <a name="requirements"></a>Spécifications

afxcomctl32.h, afxcomctl32.inl

## <a name="afx_comctl32_if_exists2"></a><a name="afx_comctl32_if_exists2"></a>AFX_COMCTL32_IF_EXISTS2

Détermine si la bibliothèque Common Controls implémente l’API spécifiée (il s’agit de la version Unicode de [AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)).

### <a name="syntax"></a>Syntaxe

```
AFX_COMCTL32_IF_EXISTS2( proc );
```

### <a name="parameters"></a>Paramètres

*proc*<br/>
Pointer vers une chaîne non terminée contenant le nom de la fonction, ou spécifie la valeur ordinaire de la fonction. Si ce paramètre est une valeur ordinaire, il doit être dans le mot de bas ordre; le mot de haut ordre doit être nul. Ce paramètre doit être dans Unicode.

### <a name="remarks"></a>Notes

Utilisez cette macro pour déterminer si la bibliothèque Common Controls la fonction spécifiée par *proc* (au lieu d’appeler [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress). Cette macro est la version Unicode de AFX_COMCTL32_IF_EXISTS.

### <a name="requirements"></a>Spécifications

afxcomctl32.h, afxcomctl32.inl

## <a name="declare_dynamic"></a><a name="declare_dynamic"></a>DECLARE_DYNAMIC

Ajoute la possibilité d’accéder à des informations de temps d’exécution sur la classe d’un objet lors de la suppression d’une classe à partir de `CObject`.

```
DECLARE_DYNAMIC(class_name)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Le nom réel de la classe.

### <a name="remarks"></a>Notes

Ajoutez la DECLARE_DYNAMIC macro au module d’en-tête (.h) pour la classe, puis incluez ce module dans tous les modules .cpp qui ont besoin d’accéder aux objets de cette classe.

Si vous utilisez les DECLARE_ DYNAMIC et IMPLEMENT_DYNAMIC macros telles que décrites, vous pouvez `CObject::IsKindOf` ensuite utiliser la macro RUNTIME_CLASS et la fonction pour déterminer la classe de vos objets au moment de l’exécution.

Si DECLARE_DYNAMIC est incluse dans la déclaration de classe, alors IMPLEMENT_DYNAMIC doit être incluse dans la mise en œuvre du groupe.

Pour plus d’informations sur le DECLARE_DYNAMIC macro, voir [CObject Class Topics](../../mfc/using-cobject.md).

### <a name="example"></a>Exemple

Voir l’exemple pour [IMPLEMENT_DYNAMIC](#implement_dynamic).

### <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="declare_dyncreate"></a><a name="declare_dyncreate"></a>DECLARE_DYNCREATE

Permet de `CObject`créer des objets de classes dérivées dynamiquement au moment de l’exécution.

```
DECLARE_DYNCREATE(class_name)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Le nom réel de la classe.

### <a name="remarks"></a>Notes

Le cadre utilise cette capacité pour créer de nouveaux objets dynamiquement. Par exemple, la nouvelle vue créée lorsque vous ouvrez un nouveau document. Les classes de documents, de visionnement et de cadre devraient soutenir la création dynamique parce que le cadre doit les créer dynamiquement.

Ajoutez la macro DECLARE_DYNCREATE dans le module .h pour la classe, puis incluez ce module dans tous les modules .cpp qui ont besoin d’accéder aux objets de cette classe.

Si DECLARE_DYNCREATE est incluse dans la déclaration de classe, alors IMPLEMENT_DYNCREATE doit être incluse dans la mise en œuvre du groupe.

Pour plus d’informations sur le macro DECLARE_DYNCREATE, voir [CObject Class Topics](../../mfc/using-cobject.md).

> [!NOTE]
> La macro DECLARE_DYNCREATE comprend toutes les fonctionnalités de DECLARE_DYNAMIC.

### <a name="example"></a>Exemple

Voir l’exemple pour [IMPLEMENT_DYNCREATE](#implement_dyncreate).

### <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="declare_olectltype"></a><a name="declare_olectltype"></a>DECLARE_OLECTLTYPE

Déclare les `GetUserTypeNameID` `GetMiscStatus` fonctions et les membres de votre classe de contrôle.

### <a name="syntax"></a>Syntaxe

```
DECLARE_OLECTLTYPE( class_name )
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Le nom de la classe de contrôle.

### <a name="remarks"></a>Notes

`GetUserTypeNameID`et `GetMiscStatus` sont des fonctions `COleControl`virtuelles pures, déclarées dans . Parce que ces fonctions sont pures virtuelles, elles doivent être remplacées dans votre classe de contrôle. En plus de DECLARE_OLECTLTYPE, vous devez ajouter la macro IMPLEMENT_OLECTLTYPE à votre déclaration de classe de contrôle.

### <a name="requirements"></a>Spécifications

**En-tête:** afxctl.h

## <a name="declare_proppageids"></a><a name="declare_proppageids"></a>DECLARE_PROPPAGEIDS

Déclare que le contrôle OLE fournit une liste de pages de propriété pour afficher ses propriétés.

### <a name="syntax"></a>Syntaxe

```
DECLARE_PROPPAGEIDS( class_name )
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Le nom de la classe de contrôle qui possède les pages de propriété.

### <a name="remarks"></a>Notes

Utilisez `DECLARE_PROPPAGEIDS` la macro à la fin de votre déclaration de classe. Ensuite, dans le fichier .cpp qui définit les fonctions `BEGIN_PROPPAGEIDS` du membre pour la classe, utilisez la `END_PROPPAGEIDS` macro, les entrées macro pour chacune des pages de propriété de votre contrôle, et la macro pour déclarer la fin de la liste de page de propriété.

Pour plus d’informations sur les pages de propriété, voir l’article [ActiveX Controls: Property Pages](../mfc-activex-controls-property-pages.md).

### <a name="requirements"></a>Spécifications

**En-tête:** afxctl.h

## <a name="declare_serial"></a><a name="declare_serial"></a>DECLARE_SERIAL

Génère le code d’en-tête `CObject`CMD nécessaire pour une classe dérivée qui peut être sérialisée.

```
DECLARE_SERIAL(class_name)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Le nom réel de la classe.

### <a name="remarks"></a>Notes

La sérialisation est le processus d’écriture ou de lecture du contenu d’un objet vers et depuis un fichier.

Utilisez la macro DECLARE_SERIAL dans un module .h, puis incluez ce module dans tous les modules .cpp qui ont besoin d’accéder aux objets de cette classe.

Si DECLARE_SERIAL est incluse dans la déclaration de classe, alors IMPLEMENT_SERIAL doit être incluse dans la mise en œuvre du groupe.

La macro DECLARE_SERIAL comprend toutes les fonctionnalités de DECLARE_DYNAMIC et DECLARE_DYNCREATE.

Vous pouvez utiliser la macro AFX_API pour `CArchive` exporter automatiquement l’opérateur d’extraction pour les classes qui utilisent les DECLARE_SERIAL et IMPLEMENT_SERIAL macros. Entre parenthèses les déclarations de classe (situées dans le fichier .h) avec le code suivant :

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

Pour plus d’informations sur le macro DECLARE_SERIAL, voir [CObject Class Topics](../../mfc/using-cobject.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCObjectSample#21](../../mfc/codesnippet/cpp/run-time-object-model-services_2.h)]

### <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="implement_dynamic"></a><a name="implement_dynamic"></a>IMPLEMENT_DYNAMIC

Génère le code CMD nécessaire `CObject`pour une classe dynamique dérivée avec un accès en temps de course au nom et à la position de la classe au sein de la hiérarchie.

```
IMPLEMENT_DYNAMIC(class_name, base_class_name)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Le nom réel de la classe.

*base_class_name*<br/>
Nom de la classe de base.

### <a name="remarks"></a>Notes

Utilisez la macro IMPLEMENT_DYNAMIC dans un module .cpp, puis liez le code d’objet résultant qu’une seule fois.

Pour plus d’informations, voir [CObject Class Topics](../../mfc/using-cobject.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCObjectSample#2](../../mfc/codesnippet/cpp/run-time-object-model-services_3.h)]

[!code-cpp[NVC_MFCCObjectSample#3](../../mfc/codesnippet/cpp/run-time-object-model-services_4.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="implement_dyncreate"></a><a name="implement_dyncreate"></a>IMPLEMENT_DYNCREATE

Permet de `CObject`créer des objets de classes dérivées dynamiquement à l’heure de l’exécution lorsqu’ils sont utilisés avec la macro DECLARE_DYNCREATE.

```
IMPLEMENT_DYNCREATE(class_name, base_class_name)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Le nom réel de la classe.

*base_class_name*<br/>
Le nom réel de la classe de base.

### <a name="remarks"></a>Notes

Le cadre utilise cette capacité pour créer de nouveaux objets dynamiquement, par exemple, lorsqu’il lit un objet à partir d’un disque pendant la sérialisation. Ajoutez la macro IMPLEMENT_DYNCREATE dans le fichier d’implémentation de la classe. Pour plus d’informations, voir [CObject Class Topics](../../mfc/using-cobject.md).

Si vous utilisez les macros DECLARE_DYNCREATE et IMPLEMENT_DYNCREATE, vous pouvez ensuite utiliser la `CObject::IsKindOf` RUNTIME_CLASS macro et la fonction membre pour déterminer la classe de vos objets au moment de l’exécution.

Si DECLARE_DYNCREATE est incluse dans la déclaration de classe, alors IMPLEMENT_DYNCREATE doit être incluse dans la mise en œuvre du groupe.

Notez que cette définition macro invoquera le constructeur par défaut pour votre classe. Si un constructeur non trivial est explicitement mis en œuvre par la classe, il doit également implémenter explicitement le constructeur par défaut ainsi. Le constructeur par défaut peut être ajouté aux sections **membres privées** ou **protégées** de la classe pour éviter qu’il ne soit appelé de l’extérieur de la mise en œuvre de la classe.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCObjectSample#22](../../mfc/codesnippet/cpp/run-time-object-model-services_5.h)]

[!code-cpp[NVC_MFCCObjectSample#23](../../mfc/codesnippet/cpp/run-time-object-model-services_6.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="implement_olecreate_flags"></a><a name="implement_olecreate_flags"></a>IMPLEMENT_OLECREATE_FLAGS

Cette macro ou [IMPLEMENT_OLECREATE](#implement_olecreate) doit apparaître dans le fichier d’implémentation de toute classe qui utilise DECLARE_OLECREATE.

### <a name="syntax"></a>Syntaxe

```
IMPLEMENT_OLECREATE_FLAGS( class_name, external_name, nFlags,
    l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Le nom réel de la classe.

*external_name*<br/>
Le nom de l’objet exposé à d’autres applications (inclus dans des guillemets).

*nFlags*<br/>
Contient un ou plusieurs des drapeaux suivants :

- `afxRegInsertable`Permet au contrôle d’apparaître dans la boîte de dialogue Insert Object pour les objets OLE.
- `afxRegApartmentThreading`Définit le modèle de threading dans le registre à ThreadingModel-Apartment.
- `afxRegFreeThreading`Définit le modèle de threading dans le registre à ThreadingModel-Free.

Vous pouvez combiner `afxRegApartmentThreading` les `afxRegFreeThreading` deux drapeaux et définir ThreadingModel-Both. Voir [InprocServer32](/windows/win32/com/inprocserver32) dans le Windows SDK pour plus d’informations sur l’enregistrement des modèles de threading.

*l*, *w1*, *w2*, *b1*, *b2*, *b3*, *b4*, *b5*, *b6*, *b7*, *b8* Composants de la classe CLSID.

### <a name="remarks"></a>Notes

> [!NOTE]
> Si vous utilisez IMPLEMENT_OLECREATE_FLAGS, vous pouvez spécifier le modèle de threading que votre objet prend en charge en utilisant le paramètre *nFlags.* Si vous voulez prendre en charge uniquement le modèle à marche unique, utilisez IMPLEMENT_OLECREATE.

Le nom externe est l’identifiant exposé à d’autres applications. Les applications clientes utilisent le nom externe pour demander un objet de cette classe à partir d’un serveur d’automatisation.

L’ID de classe OLE est un identifiant 128 bits unique pour l’objet. Il se compose d’un **long**, deux **WORD**s, et huit **BYTE**s, comme représenté par *l*, *w1*, *w2*, et *b1* à travers *b8* dans la description syntaxe. L’Assistant d’Application et les assistants de code créent des pièces d’identification uniques de classe OLE pour vous au besoin.

### <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="implement_olectltype"></a><a name="implement_olectltype"></a>IMPLEMENT_OLECTLTYPE

Implémente `GetMiscStatus` les fonctions et les `GetUserTypeNameID` membres de votre classe de contrôle.

### <a name="syntax"></a>Syntaxe

```
DECLARE_OLECTLTYPE( class_name, idsUserTypeName, dwOleMisc )
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Le nom de la classe de contrôle.

*idsUserTypeName*<br/>
L’ID de ressource d’une chaîne contenant le nom externe du contrôle.

*dwOleMisc*<br/>
Un recensement contenant un ou plusieurs drapeaux. Pour plus d’informations sur cette énumération, voir [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) dans le SDK Windows.

### <a name="remarks"></a>Notes

En plus de IMPLEMENT_OLECTLTYPE, vous devez ajouter la macro DECLARE_OLECTLTYPE à votre déclaration de classe de contrôle.

La `GetUserTypeNameID` fonction membre renvoie la chaîne de ressources qui identifie votre classe de contrôle. `GetMiscStatus`retourne les bits OLEMISC pour votre contrôle. Cette énumération spécifie une collection de paramètres décrivant les caractéristiques diverses de votre contrôle. Pour une description complète des paramètres OLEMISC, voir [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) dans le SDK Windows.

> [!NOTE]
> Les paramètres par défaut utilisés par l’ActiveX ControlWizard sont les : OLEMISC_ACTIVATEWHENVISIBLE, OLEMISC_SETCLIENTSITEFIRST, OLEMISC_INSIDEOUT, OLEMISC_CANTLINKINSIDE et OLEMISC_RECOMPOSEONRESIZE.

### <a name="requirements"></a>Spécifications

**En-tête:** afxctl.h

## <a name="implement_serial"></a><a name="implement_serial"></a>IMPLEMENT_SERIAL

Génère le code CMD nécessaire `CObject`pour une classe dynamique dérivée avec un accès en temps de course au nom et à la position de la classe au sein de la hiérarchie.

```
IMPLEMENT_SERIAL(class_name, base_class_name, wSchema)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Le nom réel de la classe.

*base_class_name*<br/>
Nom de la classe de base.

*wSchema (en)*<br/>
Un « numéro de version » UINT qui sera codé dans l’archive pour permettre à un programme de déséialisation d’identifier et de traiter les données créées par les versions antérieures du programme. Le numéro de schéma de classe ne doit pas être de -1.

### <a name="remarks"></a>Notes

Utilisez la macro IMPLEMENT_SERIAL dans un module .cpp; puis lier le code d’objet résultant qu’une seule fois.

Vous pouvez utiliser la macro AFX_API pour `CArchive` exporter automatiquement l’opérateur d’extraction pour les classes qui utilisent les DECLARE_SERIAL et IMPLEMENT_SERIAL macros. Entre parenthèses les déclarations de classe (situées dans le fichier .h) avec le code suivant :

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

Pour plus d’informations, voir les [sujets de classe CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCObjectSample#24](../../mfc/codesnippet/cpp/run-time-object-model-services_7.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="runtime_class"></a><a name="runtime_class"></a>RUNTIME_CLASS

Obtient la structure de classe de temps d’exécution du nom d’une classe de C.

```
RUNTIME_CLASS(class_name)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Le nom réel de la classe (non inclus dans les guillemets).

### <a name="remarks"></a>Notes

RUNTIME_CLASS renvoie un pointeur à une structure [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) pour la classe spécifiée par *class_name*. Seules `CObject`les classes dérivées déclarées avec DECLARE_DYNAMIC, DECLARE_DYNCREATE ou DECLARE_SERIAL retourneront les `CRuntimeClass` pointeurs à une structure.

Pour plus d’informations, voir [CObject Class Topics](../../mfc/using-cobject.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCCObjectSample#25](../../mfc/codesnippet/cpp/run-time-object-model-services_8.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="declare_olecreate"></a><a name="declare_olecreate"></a>DECLARE_OLECREATE

Permet de `CCmdTarget`créer des objets de classes dérivées grâce à l’automatisation OLE.

```
DECLARE_OLECREATE(class_name)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Le nom réel de la classe.

### <a name="remarks"></a>Notes

Cette macro permet à d’autres applications compatibles OLE de créer des objets de ce type.

Ajoutez la DECLARE_OLECREATE macro dans le module .h pour la classe, puis incluez ce module dans tous les modules .cpp qui ont besoin d’accéder aux objets de cette classe.

Si DECLARE_OLECREATE est incluse dans la déclaration de classe, alors IMPLEMENT_OLECREATE doit être incluse dans la mise en œuvre du groupe. Une déclaration de classe utilisant DECLARE_OLECREATE doit également utiliser DECLARE_DYNCREATE ou DECLARE_SERIAL.

### <a name="requirements"></a>Spécifications

**En-tête**: afxdisp.h

## <a name="implement_olecreate"></a><a name="implement_olecreate"></a>IMPLEMENT_OLECREATE

Cette macro ou [IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags) doit apparaître dans le fichier d’implémentation de toute classe qui utilise `DECLARE_OLECREATE`.

```
IMPLEMENT_OLECREATE(class_name, external_name, l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Le nom réel de la classe.

*external_name*<br/>
Le nom de l’objet exposé à d’autres applications (inclus dans des guillemets).

*l*, *w1*, *w2*, *b1*, *b2*, *b3*, *b4*, *b5*, *b6*, *b7*, *b8* Composants de la classe CLSID.

### <a name="remarks"></a>Notes

> [!NOTE]
> Si vous utilisez IMPLEMENT_OLECREATE, par défaut, vous ne soutenez que le modèle de threading unique. Si vous utilisez IMPLEMENT_OLECREATE_FLAGS, vous pouvez spécifier le modèle de threading que votre objet prend en charge en utilisant le paramètre *nFlags.*

Le nom externe est l’identifiant exposé à d’autres applications. Les applications clientes utilisent le nom externe pour demander un objet de cette classe à partir d’un serveur d’automatisation.

L’ID de classe OLE est un identifiant 128 bits unique pour l’objet. Il se compose d’un **long**, deux **WORD**s, et huit **BYTE**s, comme représenté par *l*, *w1*, *w2*, et *b1* à travers *b8* dans la description syntaxe. L’Assistant d’Application et les assistants de code créent des pièces d’identification uniques de classe OLE pour vous au besoin.

### <a name="requirements"></a>Spécifications

**En-tête**: afxdisp.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](mfc-macros-and-globals.md)<br/>
[Isolement de la bibliothèque de contrôle commun MFC](../isolation-of-the-mfc-common-controls-library.md)<br/>
[Clé CLSID](/windows/win32/com/clsid-key-hklm)
