---
description: 'En savoir plus sur : utilisation des fichiers sources MFC'
title: Utilisation des fichiers sources MFC
ms.date: 08/19/2019
helpviewer_keywords:
- public members
- source files
- MFC, source files
- MFC source files
- comments, MFC
- private member access
- protected member access
- source files, MFC
ms.assetid: 3230e8fb-3b69-4ddf-9538-365ac7ea5e72
ms.openlocfilehash: 42dc285bf4877c4bef70e430b6d2982f43e08d51
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143258"
---
# <a name="using-the-mfc-source-files"></a>Utilisation des fichiers sources MFC

La bibliothèque MFC (Microsoft Foundation Class) fournit du code source complet. Les fichiers d’en-tête (. h) se trouvent dans le répertoire *\atlmfc\include* Les fichiers d’implémentation (. cpp) se trouvent dans le répertoire *\atlmfc\src\mfc*

Cet article explique les conventions utilisées par MFC pour commenter les différentes parties de chaque classe, ce que signifient ces commentaires et ce que vous devez trouver dans chaque section. Les Assistants Visual Studio utilisent des conventions similaires pour les classes qu’ils créent pour vous, et vous trouverez probablement ces conventions utiles pour votre propre code.

Vous connaissez peut-être les **`public`** **`protected`** **`private`** Mots clés, et C++. Dans les fichiers d’en-tête MFC, vous trouverez chaque classe peut avoir plusieurs de chacune d’elles. Par exemple, les variables et les fonctions des membres publics peuvent être sous plusieurs **`public`** Mots clés. C’est parce que MFC sépare les variables et les fonctions membres en fonction de leur utilisation, et non du type d’accès autorisé. MFC utilise la **`private`** modération. Même les éléments considérés comme des détails d’implémentation sont souvent **`protected`** , et de nombreuses fois **`public`** . Bien que l’accès aux détails d’implémentation soit déconseillé, les MFC ne quittent pas la décision.

Dans les fichiers sources MFC et les fichiers d’en-tête créés par l’Assistant Application MFC, vous trouverez des commentaires tels que ceux-ci dans les déclarations de classe (généralement dans cet ordre) :

`// Constructors`

`// Attributes`

`// Operations`

`// Overridables`

`// Implementation`

## <a name="an-example-of-the-comments"></a><a name="an-example-of-the-comments"></a> Un exemple des commentaires

La liste partielle suivante de la classe `CStdioFile` utilise la plupart des commentaires standard que MFC utilise dans ses classes pour diviser les membres de la classe selon les méthodes utilisées :

```cpp
/*============================================================================*/
// STDIO file implementation

class CStdioFile : public CFile
{
    DECLARE_DYNAMIC(CStdioFile)

public:
// Constructors
    CStdioFile();

    // . . .

// Attributes
    FILE* m_pStream;    // stdio FILE
                        // m_hFile from base class is _fileno(m_pStream)

// Operations
    // reading and writing strings
    virtual void WriteString(LPCTSTR lpsz);
    virtual LPTSTR ReadString(_Out_writes_z_(nMax) LPTSTR lpsz, _In_ UINT nMax);
    virtual BOOL ReadString(CString& rString);

// Implementation
public:
    virtual ~CStdioFile();
#ifdef _DEBUG
    void Dump(CDumpContext& dc) const;
#endif
    virtual ULONGLONG GetPosition() const;
    virtual ULONGLONG GetLength() const;
    virtual BOOL Open(LPCTSTR lpszFileName, UINT nOpenFlags, CFileException* pError = NULL);

    // . . .

protected:
    void CommonBaseInit(FILE* pOpenStream, CAtlTransactionManager* pTM);
    void CommonInit(LPCTSTR lpszFileName, UINT nOpenFlags, CAtlTransactionManager* pTM);
};
```

Ces commentaires marquent de manière cohérente les sections de la déclaration de classe qui contiennent des genres similaires de membres de classe. Gardez à l’esprit qu’il s’agit de conventions MFC, et non de règles définies.

## <a name="-constructors-comment"></a>Constructeur, commentaire

La `// Constructors` section d’une déclaration de classe MFC déclare des constructeurs (dans le sens C++) et toutes les fonctions d’initialisation requises pour vraiment utiliser l’objet. Par exemple, `CWnd::Create` se trouve dans la section constructeurs, car avant d’utiliser l' `CWnd` objet, il doit être « entièrement construit » en appelant d’abord le constructeur C++, puis en appelant la `Create` fonction. En règle générale, ces membres sont publics.

Par exemple, `CStdioFile` la classe a cinq constructeurs, dont l’un est affiché dans la liste sous [un exemple de commentaires](#an-example-of-the-comments).

## <a name="-attributes-comment"></a>Attributs (commentaire)

La `// Attributes` section d’une déclaration de classe MFC contient les attributs (ou propriétés) publics de l’objet. En général, les attributs sont des variables membres ou des fonctions d’extraction/définition. Les fonctions « obtient » et « Set » peuvent être virtuelles ou non. Les fonctions « obtenir » sont souvent utilisées **`const`** , car dans la plupart des cas, elles n’ont pas d’effets secondaires. Ces membres sont normalement publics. Les attributs protected et Private se trouvent généralement dans la section Implementation.

Dans l’exemple de liste à partir de la classe `CStdioFile` , sous [un exemple des commentaires](#an-example-of-the-comments), la liste comprend une variable membre, *m_pStream*. `CDC`La classe répertorie presque 20 membres sous ce commentaire.

> [!NOTE]
> Les classes volumineuses, telles que `CDC` et `CWnd` , peuvent avoir un grand nombre de membres qui répertorient simplement tous les attributs d’un groupe qui n’ajouteraient pas beaucoup de clarté. Dans ce cas, la bibliothèque de classes utilise d’autres commentaires comme en-têtes pour délimiter les membres. Par exemple, `CDC` utilise `// Device-Context Functions` , `// Drawing Tool Functions` , `// Drawing Attribute Functions` , et bien plus encore. Les groupes qui représentent des attributs suivent la syntaxe habituelle décrite ci-dessus. De nombreuses classes OLE ont une section d’implémentation appelée `// Interface Maps` .

## <a name="-operations-comment"></a>Commentaire sur les opérations

La `// Operations` section d’une déclaration de classe MFC contient des fonctions membres que vous pouvez appeler sur l’objet pour effectuer des opérations ou prendre des mesures (effectuer des opérations). Ces fonctions ne sont généralement pas des **`const`** effets secondaires. Elles peuvent être virtuelles ou invirtuelles selon les besoins de la classe. En règle générale, ces membres sont publics.

Dans l’exemple de liste à partir de la classe `CStdioFile` , dans [un exemple des commentaires](#an-example-of-the-comments), la liste comprend trois fonctions membres sous ce commentaire : `WriteString` et deux surcharges de `ReadString` .

Comme avec les attributs, les opérations peuvent être réparties de manière plus approfondie.

## <a name="-overridables-comment"></a>Remplaçable commentaire

La `// Overridables` section d’une déclaration de classe MFC contient des fonctions virtuelles que vous pouvez substituer dans une classe dérivée lorsque vous devez modifier le comportement de la classe de base. Elles sont généralement nommées à partir de « on », bien que cela ne soit pas strictement nécessaire. Les fonctions ici sont conçues pour être remplacées et implémentent souvent ou fournissent une sorte de « rappel » ou de « raccordement ». En règle générale, ces membres sont protégés.

Dans MFC elle-même, les fonctions virtuelles pures sont toujours placées dans cette section. Une fonction virtuelle pure en C++ prend la forme suivante :

`virtual void OnDraw( ) = 0;`

Dans l’exemple de liste à partir de la classe `CStdioFile` , dans [un exemple de commentaires](#an-example-of-the-comments), la liste n’indique aucune section remplaçable. `CDocument`En revanche, la classe répertorie environ 10 fonctions membres substituables.

Dans certaines classes, vous pouvez également voir le commentaire `// Advanced Overridables` . Ces fonctions sont celles que seuls les programmeurs avancés doivent essayer de substituer. Vous n’aurez probablement jamais besoin de les remplacer.

> [!NOTE]
> Les conventions décrites dans cet article fonctionnent également bien, en général, pour les méthodes et propriétés Automation (anciennement appelées OLE Automation). Les méthodes Automation sont similaires aux opérations MFC. Les propriétés Automation sont similaires aux attributs MFC. Les événements Automation (pris en charge pour les contrôles ActiveX, autrefois appelés contrôles OLE) sont similaires aux fonctions membres substituables MFC.

## <a name="-implementation-comment"></a>Commentaire d’implémentation

La `// Implementation` section est la partie la plus importante de toute déclaration de classe MFC.

Cette section contient tous les détails de l’implémentation. Les variables membres et les fonctions membres peuvent apparaître dans cette section. Tout ce qui se trouve sous cette ligne peut changer dans une version ultérieure de MFC. À moins que vous ne puissiez pas l’éviter, vous ne devez pas vous appuyer sur les détails sous la `// Implementation` ligne. En outre, les membres déclarés sous la ligne d’implémentation ne sont pas documentés, bien que certaines implémentations soient abordées dans les notes techniques. Les substitutions de fonctions virtuelles dans la classe de base résident dans cette section, quelle que soit la section dans laquelle la fonction de classe de base est définie. Lorsqu’une fonction remplace l’implémentation de la classe de base, elle est considérée comme un détail d’implémentation. En règle générale, ces membres sont protégés, mais pas toujours.

Dans la `CStdioFile` liste sous [un exemple des commentaires](#an-example-of-the-comments), les membres déclarés sous le `// Implementation` Commentaire peuvent être déclarés comme **`public`** , **`protected`** ou **`private`** . Utilisez ces membres avec précaution, car ils peuvent changer à l’avenir. Déclarer un groupe de membres comme **`public`** il peut être nécessaire pour que l’implémentation de la bibliothèque de classes fonctionne correctement. Toutefois, cela ne signifie pas que vous pouvez utiliser en toute sécurité les membres déclarés.

> [!NOTE]
> Vous pouvez trouver des commentaires sur les types restants, au-dessus ou en dessous du `// Implementation` commentaire. Dans les deux cas, ils décrivent les genres de membres déclarés sous eux. S’ils se trouvent sous le `// Implementation` commentaire, vous devez supposer que les membres peuvent changer dans les versions ultérieures de MFC.

## <a name="see-also"></a>Voir aussi

[Rubriques générales sur MFC](../mfc/general-mfc-topics.md)
