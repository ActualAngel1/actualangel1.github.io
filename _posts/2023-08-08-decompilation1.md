---
title: Introduction To Decompilation: Part 1 - What's this all about?
output:
  md_document:
    variant: gfm+footnotes
    preserve_yaml: TRUE
knit: (function(inputFile, encoding) {
  rmarkdown::render(inputFile, encoding = encoding, output_dir = "../_posts") })
date: 2023-06-10
permalink: /posts/first
excerpt_separator: <!--more-->
always_allow_html: true
toc: true
header:
 og_image: "posts/nest-map/fig-1.png"
tags:
  - tag
---

Why would I care about this?
<!--more-->

So... Hey!
I bet you're looking at this and saying, why should I care? 
whats so interesting about decompilation anyways..?
whats even the point of these blogs

let me give you a quick intro, ok?
these blogs will go through decompilation in a less.. academic way, 
I would like to save you the details and explain the mathematics only when absolutly needed, 
and mostly as a way to give you some intuition about whats going on.
You might have tried to study this subject but have been offput by the academic way of approaching this subject,
I had to go through all that, and although its really interesting, you probably dont want to look at equations and weird math stuff all day.
I want to give you the MEAT of the subject.

ok, im gonna do the necessary bidding and explain what even IS decompilation and why YOU should care about it.

```java
import java.util.List;

abstract class Expr {
    interface Visitor<R> {
        R visitAssignExpr(Assign expr);
        R visitLogicalExpr(Logical expr);
        R visitCallExpr(Call expr);
        R visitReturnExpr(Return stmt);
        R visitPrintExpr(Print expr);
        R visitBinaryExpr(Binary expr);
        R visitGroupingExpr(Grouping expr);
        R visitLiteralExpr(Literal expr);
        R visitUnaryExpr(Unary expr);
    }
    static class Call extends Expr {
        Call(Expr callee, Instruction instruction, List<Expr> arguments) {
            this.callee = callee;
            this.instruction = instruction;
            this.arguments = arguments;
        }

        @Override
        <R> R accept(Visitor<R> visitor) {
            return visitor.visitCallExpr(this);
        }

        final Expr callee;
        final Instruction instruction;
        final List<Expr> arguments;
    }
    static class Assign extends Expr {
        Assign(Expr name, Expr value) {
            this.name = name;
            this.value = value;
        }

        @Override
        <R> R accept(Visitor<R> visitor) {
            return visitor.visitAssignExpr(this);
        }

        final Expr name;
        final Expr value;
    }

    static class Logical extends Expr {
        Logical(Expr left, String operator, Expr right) {
            this.left = left;
            this.operator = operator;
            this.right = right;
        }

        @Override
        <R> R accept(Visitor<R> visitor) {
            return visitor.visitLogicalExpr(this);
        }

        final Expr left;
        final String operator;
        final Expr right;
    }

    static class Return extends Expr {
        Return(Expr value) {
            this.value = value;
        }

        @Override
        <R> R accept(Visitor<R> visitor) {
            return visitor.visitReturnExpr(this);
        }

        final Expr value;
    }
    static class Print extends Expr {
        Print(Expr inner) {
            this.inner = inner;
        }

        @Override
        <R> R accept(Visitor<R> visitor) { return visitor.visitPrintExpr(this); }

        final Expr inner;
    }
    static class Binary extends Expr {
        Binary(Expr left, Instruction operator, Expr right) {
            this.left = left;
            this.operator = operator;
            this.right = right;
        }

        @Override
        <R> R accept(Visitor<R> visitor) {
            return visitor.visitBinaryExpr(this);
        }

        final Expr left;
        final Instruction operator;
        final Expr right;
    }

    static class Grouping extends Expr {
        Grouping(Expr expression) {
            this.expression = expression;
        }

        @Override
        <R> R accept(Visitor<R> visitor) {
            return visitor.visitGroupingExpr(this);
        }

        final Expr expression;
    }

    static class Literal extends Expr {
        Literal(String value) {
            this.value = value;
        }

        @Override
        <R> R accept(Visitor<R> visitor) {
            return visitor.visitLiteralExpr(this);
        }

        final String value;
    }

    abstract <R> R accept(Visitor<R> visitor);

    static class Unary extends Expr {
        Unary(Instruction operator, Expr right) {
            this.operator = operator;
            this.right = right;
        }

        @Override
        <R> R accept(Visitor<R> visitor) {
            return visitor.visitUnaryExpr(this);
        }

        final Instruction operator;
        final Expr right;
    }
}
```
