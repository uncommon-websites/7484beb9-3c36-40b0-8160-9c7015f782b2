<script lang="ts">
  import { slide } from 'svelte/transition';
  
  interface FAQItem {
    question: string;
    answer: string;
  }

  const faqs: FAQItem[] = [
    { question: "How does Fruit track KOL signals?", answer: "Fruit monitors influential crypto voices across Twitter, Discord, and Telegram in real-time. Our infrastructure processes millions of messages to identify when KOLs mention specific tokens, projects, or market trends, converting this unstructured social data into structured, searchable intelligence." },
    { question: "What data sources does Fruit analyze?", answer: "We track major crypto social platforms including Twitter/X, Discord servers, Telegram channels, and other community spaces where influential traders and builders share alpha. Our system focuses on verified KOLs and high-signal sources to reduce noise." },
    { question: "How early are the signals?", answer: "Fruit captures signals before they hit mainstream channels. By monitoring KOLs in real-time, you can see mentions and discussions as they happen, often hours or days before information spreads to wider crypto communities and impacts token prices." },
    { question: "Is this financial advice?", answer: "No. Fruit provides informational data only. All information on the platform is for research and educational purposes. We do not provide investment advice. Always do your own research (DYOR) before making any investment decisions." },
    { question: "How do I access the beta?", answer: "Visit fruitdatalabs.xyz/v2 to access the live beta platform. We're actively developing new features and welcome community feedback as we build in public." },
    { question: "Who built Fruit?", answer: "Fruit is built by a pseudonymous founder with nearly 4 years in web3, experience architecting structured memory systems for LLMs at OpenAI, and a background building cloud security infrastructure for federal agencies and medical database platforms." },
    { question: "What makes Fruit different from other analytics tools?", answer: "Fruit focuses specifically on converting social intelligence into structured data before tokens move. While other tools analyze on-chain metrics or aggregate social sentiment, we specialize in real-time KOL tracking and early signal detection from unstructured social chatter." }
  ];

  let openIndex: number | null = null;

  function toggle(index: number) {
    openIndex = openIndex === index ? null : index;
  }
</script>

<section class="bg-[#f5f5f5] px-6 py-24">
  <div class="max-w-[1400px] mx-auto grid grid-cols-1 lg:grid-cols-12 gap-12">
    <div class="lg:col-span-4">
      <h2 class="font-serif text-4xl text-gray-900 mb-6">
        Frequently asked questions
      </h2>
      <a href="/" class="text-sm text-gray-900 border-b border-gray-300 pb-0.5 hover:border-black transition-colors">See all support</a>
    </div>
    
    <div class="lg:col-span-8">
      <div class="border-t border-gray-200">
        {#each faqs as faq, i}
          <div class="border-b border-gray-200">
            <button 
              class="w-full py-6 flex justify-between items-center text-left hover:bg-gray-50 transition-colors"
              on:click={() => toggle(i)}
            >
              <span class="text-lg text-gray-800">{faq.question}</span>
              <span class="text-2xl font-light text-gray-400 ml-4">
                {openIndex === i ? '−' : '+'}
              </span>
            </button>
            {#if openIndex === i}
              <div transition:slide class="pb-6 text-gray-500 leading-relaxed">
                {faq.answer}
              </div>
            {/if}
          </div>
        {/each}
      </div>
    </div>
  </div>
</section>
