import React, { useState, useRef } from 'react';
import { Upload, CheckCircle2, XCircle, AlertCircle, RefreshCw, BookOpen } from 'lucide-react';

export default function App() {
  const [quizData, setQuizData] = useState([]);
  const [answers, setAnswers] = useState({});
  const [submitted, setSubmitted] = useState(false);
  const [score, setScore] = useState(0);
  const [fileName, setFileName] = useState('');
  const [error, setError] = useState('');
  const fileInputRef = useRef(null);

  // 处理文件上传与解析
  const handleFileUpload = (e) => {
    const file = e.target.files[0];
    if (!file) return;

    setFileName(file.name);
    setError('');
    setSubmitted(false);
    setAnswers({});
    setScore(0);
    setQuizData([]);

    const reader = new FileReader();
    reader.onload = (event) => {
      try {
        let text = event.target.result.trim();
        
        // 安全地清洗掉可能由复制引起的 Markdown 代码块标记
        if (text.startsWith('```json')) {
            text = text.substring(7);
        } else if (text.startsWith('```')) {
            text = text.substring(3);
        }
        if (text.endsWith('```')) {
            text = text.substring(0, text.length - 3);
        }
        
        text = text.trim();
        
        const parsedData = JSON.parse(text);
        if (parsedData.items && Array.isArray(parsedData.items)) {
          setQuizData(parsedData.items);
        } else {
          setError('文件格式不正确，找不到题库项目 (items)。请确保上传的是正确的 JSON 格式文件。');
        }
      } catch (err) {
        setError(`解析失败，请确保文件是合法的 JSON 格式。\n详细错误: ${err.message}`);
      }
    };
    reader.readAsText(file);
    
    // 清空 input value 允许重复上传同名文件
    if (fileInputRef.current) {
        fileInputRef.current.value = '';
    }
  };

  // 选择选项
  const handleSelectOption = (questionId, optionLetter) => {
    if (submitted) return; // 交卷后禁止修改
    setAnswers((prev) => ({
      ...prev,
      [questionId]: optionLetter,
    }));
  };

  // 交卷逻辑
  const handleSubmit = () => {
    if (Object.keys(answers).length < quizData.length) {
      const confirmSubmit = window.confirm("你有题目尚未作答，确定要直接交卷吗？");
      if (!confirmSubmit) return;
    }

    let currentScore = 0;
    quizData.forEach((item) => {
      if (answers[item.id] === item.correct_answer) {
        currentScore += 1;
      }
    });

    setScore(currentScore);
    setSubmitted(true);
    window.scrollTo({ top: 0, behavior: 'smooth' });
  };

  // 难度标签颜色映射
  const getDifficultyColor = (difficulty) => {
    switch (difficulty?.toLowerCase()) {
      case 'easy': return 'bg-emerald-100 text-emerald-700';
      case 'medium': return 'bg-amber-100 text-amber-700';
      case 'hard': return 'bg-rose-100 text-rose-700';
      default: return 'bg-slate-100 text-slate-700';
    }
  };

  return (
    <div className="min-h-screen bg-slate-50 text-slate-800 font-sans p-4 sm:p-6 md:p-8">
      <div className="max-w-3xl mx-auto space-y-6">
        
        {/* 顶部控制面板 */}
        <div className="bg-white p-6 sm:p-8 rounded-2xl shadow-sm border border-slate-100 text-center">
          <div className="inline-flex items-center justify-center w-16 h-16 rounded-full bg-blue-50 text-blue-500 mb-4">
            <BookOpen size={32} />
          </div>
          <h1 className="text-2xl sm:text-3xl font-bold mb-2 tracking-tight">英语冲刺模拟刷题</h1>
          <p className="text-slate-500 mb-6 text-sm sm:text-base">
            支持 iPad 触控交互。请导入您整理好的 <code>.txt</code> 或 <code>.json</code> 题库文件。
          </p>
          
          <input 
            type="file" 
            accept=".txt,.json" 
            onChange={handleFileUpload} 
            ref={fileInputRef}
            className="hidden" 
            id="file-upload" 
          />
          <label 
            htmlFor="file-upload" 
            className="inline-flex items-center justify-center px-6 py-3 bg-blue-600 hover:bg-blue-700 active:scale-95 transition-all text-white font-medium rounded-xl cursor-pointer shadow-sm shadow-blue-200"
          >
            <Upload size={18} className="mr-2" />
            {fileName ? '重新导入题库' : '导入题库文件'}
          </label>

          {fileName && (
            <div className="mt-4 text-sm font-medium text-emerald-600 flex items-center justify-center gap-1">
              <CheckCircle2 size={16} /> 已加载: {fileName} ({quizData.length} 题)
            </div>
          )}
          {error && (
            <div className="mt-4 text-sm font-medium text-rose-600 bg-rose-50 p-3 rounded-lg flex items-center justify-center gap-2 text-left">
              <AlertCircle size={18} className="shrink-0" />
              <span>{error}</span>
            </div>
          )}
        </div>

        {/* 成绩展示 (交卷后) */}
        {submitted && (
          <div className="bg-white p-6 sm:p-8 rounded-2xl shadow-sm border border-emerald-100 text-center animate-in fade-in slide-in-from-bottom-4 duration-500">
            <h2 className="text-xl font-bold text-slate-800 mb-2">本次得分</h2>
            <div className="text-5xl font-black text-blue-600 tracking-tighter mb-4">
              {score} <span className="text-2xl text-slate-400 font-medium tracking-normal">/ {quizData.length}</span>
            </div>
            <p className="text-slate-500 mb-6">
              答对率: {Math.round((score / quizData.length) * 100)}%
            </p>
            <button 
              onClick={() => {
                setSubmitted(false);
                setAnswers({});
                setScore(0);
                window.scrollTo({ top: 0, behavior: 'smooth' });
              }}
              className="inline-flex items-center justify-center px-6 py-2.5 bg-slate-100 hover:bg-slate-200 text-slate-700 font-medium rounded-xl transition-colors"
            >
              <RefreshCw size={16} className="mr-2" />
              重新挑战本卷
            </button>
          </div>
        )}

        {/* 题目列表 */}
        {quizData.length > 0 && (
          <div className="space-y-6">
            {quizData.map((item, index) => {
              const userAnswer = answers[item.id];
              const isCorrect = userAnswer === item.correct_answer;
              
              return (
                <div key={item.id} className="bg-white p-5 sm:p-7 rounded-2xl shadow-sm border border-slate-100">
                  {/* 题目 Header: 标签 & 难度 */}
                  <div className="flex flex-wrap items-start justify-between gap-3 mb-4">
                    <div className="flex flex-wrap gap-2">
                      <span className="bg-slate-100 text-slate-600 text-xs px-2.5 py-1 rounded-md font-medium">
                        第 {index + 1} 题
                      </span>
                      {item.tags?.map((tag, idx) => (
                        <span key={idx} className="bg-blue-50 text-blue-600 text-xs px-2.5 py-1 rounded-md font-medium">
                          {tag}
                        </span>
                      ))}
                    </div>
                    {item.difficulty && (
                      <span className={`text-xs px-2.5 py-1 rounded-md font-bold ${getDifficultyColor(item.difficulty)}`}>
                        {item.difficulty}
                      </span>
                    )}
                  </div>

                  {/* 题干 */}
                  <div className="text-lg font-semibold mb-6 leading-relaxed text-slate-800">
                    {item.question}
                  </div>

                  {/* 选项 */}
                  <div className="space-y-3">
                    {item.options.map((opt, optIndex) => {
                      const optLetter = opt.charAt(0);
                      const isSelected = userAnswer === optLetter;
                      
                      // 判定渲染状态
                      let optionStyle = "border-transparent bg-slate-50 hover:bg-slate-100 text-slate-700";
                      let Icon = null;

                      if (!submitted) {
                        if (isSelected) optionStyle = "border-blue-500 bg-blue-50 text-blue-700 font-medium shadow-sm";
                      } else {
                        // 交卷后的状态展示
                        if (optLetter === item.correct_answer) {
                          optionStyle = "border-emerald-500 bg-emerald-50 text-emerald-800 font-medium";
                          Icon = <CheckCircle2 className="text-emerald-500 ml-auto shrink-0" size={20} />;
                        } else if (isSelected && optLetter !== item.correct_answer) {
                          optionStyle = "border-rose-500 bg-rose-50 text-rose-800 font-medium opacity-80";
                          Icon = <XCircle className="text-rose-500 ml-auto shrink-0" size={20} />;
                        } else {
                          optionStyle = "border-transparent bg-slate-50 text-slate-400 opacity-60";
                        }
                      }

                      return (
                        <div 
                          key={optIndex}
                          onClick={() => handleSelectOption(item.id, optLetter)}
                          className={`flex items-center p-4 rounded-xl border-2 cursor-pointer transition-all duration-200 ${optionStyle}`}
                        >
                          <span className="leading-tight">{opt}</span>
                          {Icon}
                        </div>
                      );
                    })}
                  </div>

                  {/* 答案与解析 (交卷后可见) */}
                  {submitted && (
                    <div className="mt-6 p-5 bg-blue-50/50 border border-blue-100 rounded-xl animate-in fade-in duration-500">
                      <div className="font-bold text-slate-800 mb-2">
                        正确答案: <span className="text-blue-600 text-lg ml-1">{item.correct_answer}</span>
                      </div>
                      <div className="text-slate-600 text-sm sm:text-base leading-relaxed">
                        <span className="font-bold text-slate-700">解析: </span>
                        {item.rationale}
                      </div>
                    </div>
                  )}
                </div>
              );
            })}

            {/* 底部交卷按钮 */}
            {!submitted && (
              <div className="py-8 text-center sticky bottom-4 z-10">
                <button 
                  onClick={handleSubmit}
                  className="w-full sm:w-auto px-10 py-4 bg-emerald-500 hover:bg-emerald-600 active:scale-95 transition-all text-white text-lg font-bold rounded-2xl shadow-lg shadow-emerald-200"
                >
                  交卷并查看解析
                </button>
              </div>
            )}
          </div>
        )}
      </div>
    </div>
  );
}
