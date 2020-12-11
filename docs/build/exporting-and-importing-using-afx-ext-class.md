---
description: 'En savoir plus sur : exportation et importation à l’aide de AFX_EXT_CLASS'
title: Exportation et importation à l'aide de AFX_EXT_CLASS
ms.date: 11/04/2016
f1_keywords:
- afx_ext_class
helpviewer_keywords:
- AFX_EXT_CLASS macro
- exporting classes [C++]
- importing DLLs [C++]
- extension DLLs [C++], exporting classes
- executable files [C++], importing classes
- exporting DLLs [C++], AFX_EXT_CLASS macro
ms.assetid: 6b72cb2b-e92e-4ecd-bcab-c335e1d1cfde
ms.openlocfilehash: 9c82874b1e5e8791f2825cf6874399fab0e10eaa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156682"
---
# <a name="exporting-and-importing-using-afx_ext_class"></a>Exportation et importation à l'aide de AFX_EXT_CLASS

Les [dll d’extension MFC](extension-dlls-overview.md) utilisent la macro **AFX_EXT_CLASS** pour exporter des classes. les exécutables qui sont liés à la DLL d’extension MFC utilisent la macro pour importer des classes. Avec la macro **AFX_EXT_CLASS** , les fichiers d’en-tête utilisés pour générer la dll d’extension MFC peuvent être utilisés avec les exécutables qui sont liés à la dll.

Dans le fichier d’en-tête de votre DLL, ajoutez le mot clé **AFX_EXT_CLASS** à la déclaration de votre classe comme suit :

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

Cette macro est définie par MFC comme `__declspec(dllexport)` lorsque les symboles de préprocesseur `_AFXDLL` et `_AFXEXT` sont définis. Mais la macro est définie comme `__declspec(dllimport)` lorsque `_AFXDLL` est défini et `_AFXEXT` n’est pas défini. Lorsqu’il est défini, le symbole de préprocesseur `_AFXDLL` indique que la version partagée de MFC est utilisée par l’exécutable cible (une dll ou une application). Quand `_AFXDLL` et `_AFXEXT` sont définis, cela indique que l’exécutable cible est une DLL d’extension MFC.

Étant donné que `AFX_EXT_CLASS` est défini comme `__declspec(dllexport)` lors de l’exportation à partir d’une DLL d’extension MFC, vous pouvez exporter des classes entières sans placer les noms décorés pour tous les symboles de cette classe dans le fichier. def.

Bien que vous puissiez éviter de créer un fichier. def et tous les noms décorés de la classe avec cette méthode, la création d’un fichier. def est plus efficace, car les noms peuvent être exportés par ordinal. Pour utiliser la méthode de fichier. def d’exportation, placez le code suivant au début et à la fin de votre fichier d’en-tête :

```cpp
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

> [!CAUTION]
> Soyez prudent lorsque vous exportez des fonctions inline, car elles peuvent créer des risques de conflits de versions. Une fonction inline est développée dans le code de l’application ; par conséquent, si vous réécrivez ultérieurement la fonction, elle n’est pas mise à jour, sauf si l’application elle-même est recompilée. Normalement, les fonctions DLL peuvent être mises à jour sans recréer les applications qui les utilisent.

## <a name="exporting-individual-members-in-a-class"></a>Exportation de membres individuels dans une classe

Il peut arriver que vous souhaitiez exporter des membres individuels de votre classe. Par exemple, si vous exportez une `CDialog` classe dérivée de, vous devrez peut-être exporter le constructeur et l' `DoModal` appel. Vous pouvez utiliser `AFX_EXT_CLASS` sur les membres individuels que vous devez exporter.

Par exemple :

```cpp
class CExampleDialog : public CDialog
{
public:
   AFX_EXT_CLASS CExampleDialog();
   AFX_EXT_CLASS int DoModal();
   ...
   // rest of class definition
   ...
};
```

Étant donné que vous n’exportez plus tous les membres de la classe, vous pouvez rencontrer un problème supplémentaire en raison de la façon dont les macros MFC fonctionnent. Plusieurs macros d’assistance MFC déclarent ou définissent en fait des membres de données. Par conséquent, ces membres de données doivent également être exportés à partir de votre DLL.

Par exemple, la `DECLARE_DYNAMIC` macro est définie comme suit lors de la génération d’une DLL d’extension MFC :

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
   static CRuntimeClass* PASCAL _GetBaseClass(); \
public: \
   static AFX_DATA CRuntimeClass class##class_name; \
   virtual CRuntimeClass* GetRuntimeClass() const; \
```

La ligne qui commence par static `AFX_DATA` déclare un objet statique à l’intérieur de votre classe. Pour exporter cette classe correctement et accéder aux informations d’exécution à partir d’un exécutable client, vous devez exporter cet objet statique. Étant donné que l’objet statique est déclaré avec le modificateur `AFX_DATA` , vous devez uniquement définir `AFX_DATA` comme étant lors de la `__declspec(dllexport)` génération de votre dll et le définir comme `__declspec(dllimport)` lors de la génération de votre exécutable client. Étant donné que `AFX_EXT_CLASS` est déjà défini de cette manière, il vous suffit de redéfinir `AFX_DATA` pour être le même que dans la `AFX_EXT_CLASS` définition de votre classe.

Par exemple :

```cpp
#undef  AFX_DATA
#define AFX_DATA AFX_EXT_CLASS

class CExampleView : public CView
{
   DECLARE_DYNAMIC()
   // ... class definition ...
};

#undef  AFX_DATA
#define AFX_DATA
```

Étant donné que MFC utilise toujours le `AFX_DATA` symbole sur les éléments de données qu’il définit dans ses macros, cette technique fonctionne pour tous les scénarios de ce type. Par exemple, il fonctionne pour `DECLARE_MESSAGE_MAP` .

> [!NOTE]
> Si vous exportez la classe entière plutôt que les membres sélectionnés de la classe, les données membres statiques sont exportées automatiquement.

### <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Exporter à partir d’une DLL à l’aide de fichiers. def](exporting-from-a-dll-using-def-files.md)

- [Exporter à partir d’une DLL à l’aide d' __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exporter des fonctions C++ à utiliser dans des exécutables en langage C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Exporter des fonctions C à utiliser dans des exécutables en langage C ou C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Déterminer la méthode d’exportation à utiliser](determining-which-exporting-method-to-use.md)

- [Importer dans une application à l’aide de __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Initialiser une DLL](run-time-library-behavior.md#initializing-a-dll)

### <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [Noms décorés](reference/decorated-names.md)

- [Importation et exportation de fonctions inline](importing-and-exporting-inline-functions.md)

- [Importations mutuelles](mutual-imports.md)

## <a name="see-also"></a>Voir aussi

[Exportation à partir d'une DLL](exporting-from-a-dll.md)
