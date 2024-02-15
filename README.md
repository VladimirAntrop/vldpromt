# vldpromt

//
//  TextEditorView.swift
//  CollageBuilder
//
//

import SwiftUI

struct TextEditorView: View {
    
    @Environment(\.dismiss) private var dismiss
    
    @Binding var text: TextSettings
    
    
    var body: some View {
        ZStack {
            TextView(settings: $text,
                     interactionEnabled: true,
                     keyboardShowed: true)
            .frame(width: text.size.width,
                   height: text.size.height)
            topBar
        }
    }
    
    private var topBar: some View {
        VStack {
            HStack {
                Spacer()
                Button {
                    dismiss()
                } label: {
                    Text("Close")
                }
            }
            .padding(20)
            Spacer()
        }
    }
}

struct TextEditorView_Previews: PreviewProvider {
    static var previews: some View {
        TextEditorView(text: .constant(.init(collageSize: .init(side: 1000),
                                             zPosition: 1)))
    }
}
