// MainActivity.kt

package com.example.mercadodobairro

import android.content.Intent
import android.net.Uri
import android.os.Bundle
import android.widget.*
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {

    private val sampleProducts = listOf(
        Product("Camisa Vermelha", "1000 Kz", "944425996", "https://via.placeholder.com/150"),
        Product("Telemóvel Usado", "15000 Kz", "944425996", "https://via.placeholder.com/150")
    )

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val listView = findViewById<ListView>(R.id.listViewProducts)
        listView.adapter = ProductAdapter(this, sampleProducts)

        listView.setOnItemClickListener { _, _, position, _ ->
            val product = sampleProducts[position]
            val url = "https://wa.me/244${product.contact}"
            val intent = Intent(Intent.ACTION_VIEW)
            intent.data = Uri.parse(url)
            startActivity(intent)
        }
