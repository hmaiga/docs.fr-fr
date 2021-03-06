---
title: Vue d'ensemble de la classe XDocument
ms.date: 07/20/2015
ms.assetid: 45cb7e71-196a-47da-bfe9-7a5589db1eed
ms.openlocfilehash: cbc1ccca53978da07f31c0ba7e54eca9f06b0e72
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349292"
---
# <a name="xdocument-class-overview-visual-basic"></a>Vue d’ensemble de la classe XDocument (Visual Basic)
Cette rubrique présente la classe <xref:System.Xml.Linq.XDocument>.  
  
## <a name="overview-of-the-xdocument-class"></a>Vue d'ensemble de la classe XDocument  
 La classe <xref:System.Xml.Linq.XDocument> contient les informations nécessaires pour un document XML valide. Cela inclut une déclaration XML, des instructions de traitement et des commentaires.  
  
 Notez que la création d'objets <xref:System.Xml.Linq.XDocument> est nécessaire uniquement si vous avez besoin de la fonctionnalité spécifique fournie par la classe <xref:System.Xml.Linq.XDocument>. Dans de nombreux cas, vous pouvez travailler directement avec <xref:System.Xml.Linq.XElement>. L'utilisation directe de l'objet <xref:System.Xml.Linq.XElement> est un modèle de programmation plus simple.  
  
 <xref:System.Xml.Linq.XDocument> dérive de <xref:System.Xml.Linq.XContainer>. Par conséquent, il peut contenir des nœuds enfants. Toutefois, les objets <xref:System.Xml.Linq.XDocument> ne peuvent avoir qu'un seul nœud <xref:System.Xml.Linq.XElement> enfant. Cela reflète la norme XML selon laquelle il ne doit y avoir qu'un seul élément racine dans un document XML.  
  
## <a name="components-of-xdocument"></a>Composants de XDocument  
 Un objet <xref:System.Xml.Linq.XDocument> peut contenir les éléments suivants :  
  
- Un objet <xref:System.Xml.Linq.XDeclaration>. <xref:System.Xml.Linq.XDeclaration> vous permet de spécifier les parties pertinentes d'une déclaration XML : la version XML, l'encodage du document et si le document XML est autonome.  
  
- Un objet <xref:System.Xml.Linq.XElement>. Il s'agit du nœud racine du document XML.  
  
- Une quantité quelconque d'objets <xref:System.Xml.Linq.XProcessingInstruction>. Une instruction de traitement communique des informations à une application qui traite le code XML.  
  
- Une quantité quelconque d'objets <xref:System.Xml.Linq.XComment>. Les commentaires seront des frères de l'élément racine. L'objet <xref:System.Xml.Linq.XComment> ne peut pas être le premier argument de la liste, car un document XML valide ne peut pas commencer par un commentaire.  
  
- Un objet <xref:System.Xml.Linq.XDocumentType> pour le DTD.  
  
 Lorsque vous sérialisez un objet <xref:System.Xml.Linq.XDocument>, même si `XDocument.Declaration` a la valeur `null`, la sortie aura une déclaration XML à condition que la propriété `Writer.Settings.OmitXmlDeclaration` du writer ait la valeur `false` (valeur par défaut).  
  
 Par défaut, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] définit la version à « 1.0 » l'encodage à « utf-8 ».  
  
## <a name="using-xelement-without-xdocument"></a>Utilisation de XElement sans XDocument  
 Comme mentionné précédemment, la classe <xref:System.Xml.Linq.XElement> est la classe principale dans l'interface de programmation [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Dans de nombreux cas, votre application ne nécessitera pas la création d'un document. L'utilisation de la classe <xref:System.Xml.Linq.XElement> vous permet de créer une arborescence XML, de la modifier, de l'enregistrer et d'y ajouter d'autres arborescences XML.  
  
## <a name="using-xdocument"></a>Utilisation de XDocument  
 Pour construire un objet <xref:System.Xml.Linq.XDocument>, utilisez la construction fonctionnelle, comme pour construire des objets <xref:System.Xml.Linq.XElement>.  
  
 Le code suivant crée un objet <xref:System.Xml.Linq.XDocument> et ses objets contenus associés.  
  
```vb  
Dim doc As XDocument = <?xml version="1.0" encoding="utf-8"?>  
                       <!--This is a comment.-->  
                       <?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
                       <Pubs>  
                           <Book>  
                               <Title>Artifacts of Roman Civilization</Title>  
                               <Author>Moreno, Jordao</Author>  
                           </Book>  
                           <Book>  
                               <Title>Midieval Tools and Implements</Title>  
                               <Author>Gazit, Inbar</Author>  
                           </Book>  
                       </Pubs>  
                       <!--This is another comment.-->  
doc.Save("test.xml")  
```  
  
 Lorsque vous examinez le fichier test.xml, vous obtenez la sortie suivante :  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!--This is a comment.-->  
<?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
<Pubs>  
  <Book>  
    <Title>Artifacts of Roman Civilization</Title>  
    <Author>Moreno, Jordao</Author>  
  </Book>  
  <Book>  
    <Title>Midieval Tools and Implements</Title>  
    <Author>Gazit, Inbar</Author>  
  </Book>  
</Pubs>  
<!--This is another comment.-->  
```  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la programmation de LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
