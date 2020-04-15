---
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
ms.openlocfilehash: 95c72f8251a8a59833483eb948709c80a69d03d7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328609"
---
# <a name="exporting-and-importing-using-afx_ext_class"></a>Exportation et importation à l'aide de AFX_EXT_CLASS

[Les DLL d’extension de MFC](extension-dlls-overview.md) utilisent les **macro-AFX_EXT_CLASS** pour exporter des classes ; les exécutables qui lient à l’extension MFC DLL utilisent la macro pour importer des classes. Avec la **AFX_EXT_CLASS** macro, les mêmes fichiers d’en-tête qui sont utilisés pour construire l’extension MFC DLL peut être utilisé avec les exécutables qui lient à la DLL.

Dans le fichier d’en-tête de votre DLL, ajoutez le mot clé **AFX_EXT_CLASS** à la déclaration de votre classe comme suit :

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

Cette macro est définie `__declspec(dllexport)` par MFC comme `_AFXDLL` `_AFXEXT` lorsque le préprocesseur symboles et sont définis. Mais la macro `__declspec(dllimport)` est `_AFXDLL` définie `_AFXEXT` comme quand est définie et n’est pas définie. Lorsqu’il est défini, `_AFXDLL` le symbole du préprocesseur indique que la version partagée de MFC est utilisée par la cible exécutable (un DLL ou une application). Lorsque `_AFXDLL` les `_AFXEXT` deux et sont définis, cela indique que la cible exécutable est une extension MFC DLL.

Parce `AFX_EXT_CLASS` que `__declspec(dllexport)` c’est défini comme lors de l’exportation à partir d’une extension MFC DLL, vous pouvez exporter des classes entières sans placer les noms décorés pour tous les symboles de cette classe dans le fichier .def.

Bien que vous puissiez éviter de créer un fichier .def et tous les noms décorés pour la classe avec cette méthode, la création d’un fichier .def est plus efficace parce que les noms peuvent être exportés par ordinaire. Pour utiliser la méthode de fichier .def d’exportation, placez le code suivant au début et à la fin de votre fichier d’en-tête :

```cpp
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

> [!CAUTION]
> Soyez prudent lors de l’exportation de fonctions en ligne, car ils peuvent créer la possibilité de conflits de version. Une fonction en ligne est étendue au code d’application; par conséquent, si vous réécrivez plus tard la fonction, elle ne se met pas à jour à moins que l’application elle-même ne soit recompilée. Normalement, les fonctions DLL peuvent être mises à jour sans reconstruire les applications qui les utilisent.

## <a name="exporting-individual-members-in-a-class"></a>Exporter des membres individuels dans une catégorie

Parfois, vous voudrez peut-être exporter des membres individuels de votre classe. Par exemple, si vous `CDialog`exportez une classe dérivée, vous n’aurez peut-être qu’à exporter le constructeur et l’appel. `DoModal` Vous pouvez `AFX_EXT_CLASS` utiliser sur les membres individuels que vous devez exporter.

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

Parce que vous n’exportez plus tous les membres de la classe, vous pouvez rencontrer un problème supplémentaire en raison de la façon dont les macros MFC fonctionnent. Plusieurs des macros d’aide de MFC déclarent ou définissent réellement les membres de données. Par conséquent, ces membres de données doivent également être exportés de votre DLL.

Par exemple, `DECLARE_DYNAMIC` la macro est définie comme suit lors de la construction d’une extension MFC DLL:

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
   static CRuntimeClass* PASCAL _GetBaseClass(); \
public: \
   static AFX_DATA CRuntimeClass class##class_name; \
   virtual CRuntimeClass* GetRuntimeClass() const; \
```

La ligne qui `AFX_DATA` commence par statique déclare un objet statique à l’intérieur de votre classe. Pour exporter correctement cette classe et accéder aux informations de temps d’exécution d’un client, vous devez exporter cet objet statique. Parce que l’objet statique `AFX_DATA`est déclaré avec `AFX_DATA` le `__declspec(dllexport)` modificateur, vous n’avez qu’à définir pour être lors de la construction de votre DLL et le définir comme `__declspec(dllimport)` lors de la construction de votre client exécutable. Parce `AFX_EXT_CLASS` que c’est déjà défini de `AFX_DATA` cette façon, `AFX_EXT_CLASS` vous avez juste besoin de redéfinir pour être le même qu’autour de votre définition de classe.

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

Parce que MFC `AFX_DATA` utilise toujours le symbole sur les éléments de données qu’il définit dans ses macros, cette technique fonctionne pour tous ces scénarios. Par exemple, il `DECLARE_MESSAGE_MAP`fonctionne pour .

> [!NOTE]
> Si vous exportez toute la classe plutôt que des membres sélectionnés de la classe, les membres de données statiques sont automatiquement exportés.

### <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Exportation à partir d’un DLL à l’aide de fichiers .def](exporting-from-a-dll-using-def-files.md)

- [Exportation d’un DLL à l’aide de __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Fonctions d’exportation CMD pour une utilisation dans les exécutables en langue C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Fonctions d’exportation C pour une utilisation dans les exécutables en langue C ou en langue C](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Déterminer quelle méthode d’exportation utiliser](determining-which-exporting-method-to-use.md)

- [Importer dans une application à l'aide de __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Initialiser un DLL](run-time-library-behavior.md#initializing-a-dll)

### <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [Noms décorés](reference/decorated-names.md)

- [Importation et exportation de fonctions inline](importing-and-exporting-inline-functions.md)

- [Importations mutuelles](mutual-imports.md)

## <a name="see-also"></a>Voir aussi

[Exportation à partir d’une DLL](exporting-from-a-dll.md)
